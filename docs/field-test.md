---
layout: default
title: Field Test
nav_order: 4
---
# Hay description fields

### Field [`hay_single_lot_traceble`]()
<dl>
  <dt>Data type</dt>
  <dd>boolean</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false ]</dd>
</dl>

<details>
  <summary>More information</summary>
  <p>
    Many producers of goods ranging from foods to medicines to industrial equipment employ the concept of a defined "lot" of a given product for quality control, assurance, and traceability purposes. We define "lot discipline" as the regular, commercial practice of identifying and segregating goods by defined lots.

    The production, marketing, and purchase of hay traceable to defined lots is a beneficial practice with broad scientific and agronomic support. A single lot of hay is "forage taken from the same farm, field, and cut under uniform conditions within a 48-hour time period. A lot can represent several truck or wagon loads, but all the forage should have been harvested and stored under identical conditions." We adopt this definition from the sidebar on page 10 of Understanding Forage Quality (Ball et al., 2001), but note that it appears in substantially the same form in numerous academic and agricultural extension service publications.

    This field may be implemented as a boolean data type, with "true" representing the seller's affirmation that hay he offers to the market is traceable to a single lot as defined. At some point in the future, should lot discipline become commonplace in the hay market, it may be sensible for this affirmation to be a default value of the product definition. In such case, sellers representing their hay in accordance with the standard description model would implicitly affirm that the hay they offer to the market is traceable by lot as such term is then defined.

    Systems implementing this standard may generate lot identifiers automatically and then let users map their own identifiers to the system-generated ones. Presuming we validate that approach as useful, we will extend this definition by adding an optionally-repeating component block or comparable device to allow users to add one or more fields to hold these values. This would be useful, e.g., for linking test results to listings.
  </p>
</details>
  
### Field [`intended_livestock_use`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ Dairy | Beef | Horse | Goat | Sheep | Deer | Camel | Landscape ]</dd>
</dl>

### Field [`hay_mixed_sward`]()
<dl>
  <dt>Data type</dt>
  <dd>boolean</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false ]</dd>
</dl>

<details>
  <summary>More information</summary>
  <p>
    A "sward" is an "expanse of short grass." Growers may choose to produce "pure" (monoculture) or "mixed" (polyculture) swards of hay and consequently, pure or mixed forage. A pure sward contains hay of the same species, subspecies, or variety, e.g., the Tifton 85 cultivar of bermuda grass. A mixed sward contains two or more species, subspecies, or varieties, e.g., an alfalfa/timothy mix.

    This field supports expression of the grower's intention and not necessarily the result. If implemented as a boolean data type as suggested, "true" expresses that the grower intended to produce mixed hay, while "false" expresses that the grower intended to produce pure hay.

    The emphasis on intention rather than result accounts for the possibility of infiltration of a sward by unintended vegetation ("weeds"). This unintended vegetation may even serve as a forage crop itself. For example, bahia grass may deliberately be raised as hay, but when infiltrating an otherwise pure sward of coastal bermuda grass, bahia grass acts as a weed. And, in some markets, all bermuda grass hays are treated as noxious weeds.

    If a grower intends to produce a pure crop but what results is a crop with significant weeds, this field should still take a value of "false," as the grower intended a pure sward. Similarly, if the grower intends to produce a mixed crop but only one variety survives to harvest, this field should still take a value of "true." We use the [`variety_representation_target`]() and [`variety_representation_result`]() fields, respectively, part of a conditionally-repeating group of fields, to account for differences between intentions and results.
  </p>
</details>

### Field [`hay_variety_instances`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>A positive integer representing the quantity of hay varieties purposefully grown in the sward. A pure sward always takes a value of "1." A mixed sward must take a value of "2" or more.</dd>
</dl>

<details>
  <summary>More information</summary>
  <p>
    This field serves both marketing and technological purposes. From a marketing perspective, it allows the farmer to express how many varieties of hay he has meant to include in his bales. Technologically, it reports how many instances of the following [`hay_variety_component_block`]() a message or database table will contain. 
  
    Arguably, the presence of this field makes the preceding, [`hay_mixed_sward`]() field superfluous. Implicitly, a value of "1" for this field means "pure sward," whereas a value greater than "1" means "mixed sward." We include both fields for the time being, principally to emphasize the importance of disclosing whether hay is pure or mixed and to help draw a distinction between what the grower intends and what actually results. We concede that this field alone may suffice and that the product definition may be improved through future removal of the [`hay_mixed_sward`]() field.

    Systems implementing this standard should validate values for this field against values for the preceding, hay_mixed_sward field. If hay_mixed_sward is false, the value of this field should be "1." On the other hand, if [`hay_mixed_sward`]() is true, then the value of this field should be "2" or greater.
  </p>
</details>

### Placeholder for Conditionally-repeating block

## Hay origin

### Field [`hay_origin_country`]()
<dl>
  <dt>Data type</dt>
  <dd>string</dd>
  <dt>Valid values</dt>
  <dd>A two-character string from the ISO 3166-1 alpha-2 code list, representing the applicable, two-letter code for country of origin.</dd>
</dl>

### Field [`hay_origin_subdivision`]()
<dl>
  <dt>Data type</dt>
  <dd>string</dd>
  <dt>Valid values</dt>
  <dd>A string of up to three alphanumeric characters from the ISO 3166-2 list of country subdivision codes, representing states, dependent territories, administrative divisions, or other subdivisions of various countries.</dd>
</dl>

### Field [`hay_origin_county`]()
<dl>
  <dt>Data type</dt>
  <dd>string</dd>
  <dt>Valid values</dt>
  <dd>A string identifying the county, parish, or other political subdivision of origin, immediately following in jurisdictional rank the subdivision from the ISO 3166-2 list.</dd>
</dl>

<p>Important especially in the U.S. for epidemiological and agricultural extension services purposes.</p>

### Field [`hay_origin_postal`]()
<dl>
  <dt>Data type</dt>
  <dd>string</dd>
  <dt>Valid values</dt>
  <dd>An alphanumeric string representing the postal code of origin, if such code exists, is known, and the seller is willing to disclose this information. If hay originates in a country lacking a postal-code system, enter "None." If hay originates in a country with a postal-code system but the seller does not know the code, enter "Unknown." If the seller knows but is unwilling to disclose the postal code, enter "Withheld."</dd>
</dl>

<p>Systems implementing this standard may be able to populate this field automatically for the user, using street address for example. In the U.S., about ten percent of postal codes cross jurisdictional (town, county, or state) boundaries, so implementers should exercise caution in inferring other location information from such codes.</p>

### Field [`source_field_elevation`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>An integer representing the magnitude of the average elevation of the source field(s) for this hay in relation to sea level, rounded to the nearest whole number, whether in meters or feet.</dd>
</dl>

Use the field [`source_field_elevation_units`]() to specify the unit of measure for this magnitude.

<p> The elevation of a field determines in part the temperatures and other weather conditions under which forage is grown and which weeds and pests are likely to require management.</p>

### Field [`source_field_elevation_units`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ feet | meters ]</dd>
</dl>

### Field [`source_field_climate_class`]()
<dl>
  <dt>Data type</dt>
  <dd>string</dd>
  <dt>Valid values</dt>
  <dd>The three-character, Köppen climate classification for the source field(s) for this hay. If the source fields are too distant from one another to fall under a single climate class, enter "var" for "various."</dd>
</dl>

<details>
  <summary>More information</summary>
  
  <p>While we often think of climate as an atmospheric phenomenon, climate classification actually reflects what kind of vegetation naturally prevails in a certain area. The Köppen classification system is well-established and readily accessible. In future versions of the product definition, it may be prudent to allow users to choose from several classification schemes or else to use another by default.

  Systems implementing this standard may populate this field with values sourced automatically from other databases, based upon location information the user supplies.</p>
</details>

### Field [`source_field_area`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>An integer representing the magnitude of the area of the source field(s) for this hay, rounded to the nearest whole number, whether in hectares or acres.  Use "0" if unknown.</dd>
</dl>

Use the field [`source_field_area_units`]() to specify the unit of measure for this magnitude.

The variability of hay from one bale to the next depends on a variety of factors, including soil conditions, weather, weeds, and pests. As a rule, the larger the area of the source field (or fields) for a forage, the greater will be the variability in quality and anti-quality factors for that forage.

### Field [`source_field_area_units`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd> = [ hectares | acres ]</dd>
</dl>

### Field [`irrigation_method_available`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ none | flood | sprinkler | pivot | drip ]</dd>
</dl>

### Field [`irrigation_method_used`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ none | flood | sprinkler | pivot | drip ]</dd>
</dl>

### Field [`source_stand_age`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>An integer representing the age in years of the stand(s) from which this hay is harvested, rounded up to the nearest year. Use "0" if unknown or the hay was harvested from stands of different ages.</dd>
</dl>

## Fertilization

### Field [`last_fertilized_nitrogen`]()
<dl>
  <dt>Data type</dt>
  <dd>datetime</dd>
  <dt>Valid values</dt>
  <dd>A date in YYYYMMDD format representing the last date of nitrogen fertilization for this hay, or "00000000" if not nitrogen-fertilized.</dd>
</dl>

### Field [`last_fertilized_potassium`]()
<dl>
  <dt>Data type</dt>
  <dd>datetime</dd>
  <dt>Valid values</dt>
  <dd>A date in YYYYMMDD format representing the last date of potassium fertilization for this hay, or "00000000" if not potassium-fertilized.</dd>
</dl>

### Field [`last_fertilized_phosphorus`]()
<dl>
  <dt>Data type</dt>
  <dd>datetime</dd>
  <dt>Valid values</dt>
  <dd>A date in YYYYMMDD format representing the last date of phosphorus fertilization for this hay, or "00000000" if not phosphorus-fertilized.</dd>
</dl>

### Field [`amount_fertilized_nitrogen`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>
    An integer representing the magnitude, rounded to the nearest whole unit, of the last nitrogen application for this hay, or "0" if not nitrogen-fertilized.</dd>
</dl>

Use the field [`amount_fertilized_units`]() to specify the unit of measure for this magnitude.

### Field [`amount_fertilized_nitrogen`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>An integer representing the magnitude, rounded to the nearest whole unit, of the last nitrogen application for this hay, or "0" if not nitrogen-fertilized.</dd>
</dl>

Use the field [`amount_fertilized_units`]() to specify the unit of measure for this magnitude.

### Field [`amount_fertilized_potassium`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>An integer representing the magnitude, rounded to the nearest whole unit, of the last potassium application for this hay, or "0" if not potassium-fertilized.</dd>
</dl>

Use the field [`amount_fertilized_units`]() to specify the unit of measure for this magnitude.

### Field [`amount_fertilized_phosphorus`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>An integer representing the magnitude, rounded to the nearest whole unit, of the last phosphorus application for this hay, or "0" if not phosphorus-fertilized.</dd>
</dl>

Use the field [`amount_fertilized_units`]() to specify the unit of measure for this magnitude.

### Field [`amount_fertilized_units`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ kilograms per hectare | pounds per acre ]</dd>
</dl>

## Certification

### Field [`hay_certified_organic`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`hay_certified_weed_free`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

## Hay treatment

### Field [`hay_conditioned`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`hay_herbicide_treated`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`hay_preservative_applied`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`hay_coloring_agent_used`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

## Harvesting

### Field [`harvest_date_start`]()
<dl>
  <dt>Data type</dt>
  <dd>datetime</dd>
  <dt>Valid values</dt>
  <dd>A date in YYYYMMDD format representing the commencement date of the harvest for this hay.</dd>
</dl>

<details>
  <summary>More information</summary>

  Mowing is generally the first step in harvesting hay and thus represents the commencement of a specific harvest. Identifying the harvest start date informs the consumer as to the age of the hay and season of the harvest. This information may also be useful in ascertaining local weather conditions for the harvest.

  This note applies both to this field and to the [`harvest_date_end`]() field. The seller may lack specific knowledge of harvest start and end dates and only be able to estimate these dates. A protocol for using estimated dates is feasible through the use of double-zero values for day of month or even month of year. A double zero in the day field would mean that the seller is confident as to the month of the applicable harvest date but not the day. Double zeroes in both the day and month places would mean the seller is confident of the year of harvest but neither the month nor day.
  
</details>
  
### Field [`harvest_date_end`]()
<dl>
  <dt>Data type</dt>
  <dd>datetime</dd>
  <dt>Valid values</dt>
  <dd>A date in YYYYMMDD format representing the conclusion date for the harvest for this hay.</dd>
</dl>

This date value may be same as, but not prior to, that for [`harvest_date_start`](). May not be more than two days after [`harvest_date_start`](), according to current, working definition of lot, if single-lot-traceability is claimed.

Systems implementing this standard should evaluate the difference in days between [`harvest_date_start`]() and [`harvest_date_end`]() and compare the result with the value provided for [`hay_single_lot`](). If [`hay_single_lot`]() is true, then the difference in days must be two or fewer.

### Field [`hay_cutting`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>An integer representing which cutting of the harvest season produced this hay, i.e., "1" for first cut, "2" for second cut, "12" for twelfth cut, and so forth. If unknown, enter "0" (zero).</dd>
</dl>

### Field [`source_field_yield`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>An integer representing the magnitude of the yield from the source field(s) for this hay, rounded to the nearest whole number, whether in metric, long, or short tons.</dd>
</dl>

Use the [`field source_field_yield_units`]() to specify the unit of measure for this magnitude.

For purposes of this field, we define "yield" as the product of (a) number of bales and (b) average bale weight.

### Field [`source_field_yield_units`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ metric tons | British (long) tons | U.S. (short) tons ]</dd>
</dl>

## Weather damage

### Field [`weather_damage_windrow_rain`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay received rainfall in the windrow, "false" the seller's affirmation that no rain fell on the windrow, and "unknown" the seller's disclosure that he has no knowledge of whether the windrow for this hay received rainfall.</p>

### Field [`weather_damage_windrow_snow`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay received snow in the windrow, "false" the seller's affirmation that no snow fell on the windrow, and "unknown" the seller's disclosure that he has no knowledge of whether the windrow for this hay received snowfall.</p>

### Field [`weather_damage_windrow_sleet`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay received sleet in the windrow, "false" the seller's affirmation that no sleet fell on the windrow, and "unknown" the seller's disclosure that he has no knowledge of whether the windrow for this hay received sleet.</p>

### Field [`weather_damage_windrow_hail`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay received hail in the windrow, "false" the seller's affirmation that no hail fell on the windrow, and "unknown" the seller's disclosure that he has no knowledge of whether the windrow for this hay received hail.</p>

### Field [`weather_damage_windrow_fog`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay experienced fog in the windrow, "false" the seller's affirmation that no fog weighed on the windrow, and "unknown" the seller's disclosure that he has no knowledge of whether the windrow for this hay experienced fog.</p>

### Field [`weather_damage_windrow_fog`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay experienced heavy dewfall in the windrow, "false" the seller's affirmation that the windrow escaped heavy dewfall, and "unknown" the seller's disclosure that he has no knowledge of whether the windrow for this hay experienced heavy dewfall.</p>

### Field [`weather_damage_windrow_fog`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ none | minor | modest | substantial | unknown ]</dd>
</dl>

<p>This field allows the seller to disclose his assessment of weather damage to the hay while in the windrow.</p>

### Field [`weather_damage_baled_rain`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay received rainfall once baled, "false" the seller's affirmation that no rain fell on the bales, and "unknown" the seller's disclosure that he has no knowledge of whether the bales received rainfall.</p>

### Field [`weather_damage_baled_snow`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay received snow once baled, "false" the seller's affirmation that no snow fell on the bales, and "unknown" the seller's disclosure that he has no knowledge of whether the bales received snowfall.</p>

### Field [`weather_damage_baled_sleet`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay received sleet once baled, "false" the seller's affirmation that no sleet fell on the bales, and "unknown" the seller's disclosure that he has no knowledge of whether the bales received sleet.</p>

### Field [`weather_damage_baled_hail`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay received hail once baled, "false" the seller's affirmation that no hail fell on the bales, and "unknown" the seller's disclosure that he has no knowledge of whether the bales received hail.</p>

### Field [`weather_damage_baled_moisture`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

<p>This field may be implemented as an enumerated data type, with "true" representing the seller's disclosure that this hay experienced fog, heavy dewfall, or another source of excessive moisture once baled, "false" the seller's affirmation that no such phenomena affected the bales, and "unknown" the seller's disclosure that he has no knowledge of whether fog, heavy dewfall, or any other source of excessive moisture affected the bales.</p>

### Field [`weather_damage_baled_assessment`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ None | Minor | Modest | Substantial | Unknown ]</dd>
</dl>

<p>This field allows the seller to disclose his assessment of weather damage to the hay once baled.</p>

## Hay packaging

### Field [`hay_packaging_history`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ Bales made in field | Re-baled from other hay bales | Cut from larger hay bales ]</dd>
</dl>

### Field [`bale_binding`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ Twine, two-tie | Twine, three-tie | Twine, four-tie | Twine, five-tie | Twine, six-tie | Wire, two-tie | Wire, three-tie | Fabric band, two-tie | Fabric band, three-tie | Plastic band, two-tie | Plastic band, three-tie | Metal band, two-tie | Metal band, three-tie | Netwrap | John Deere CoverEdge ]</dd>
</dl>

Systems implementing this standard may benefit from validation of these values against the value provided for the [`field bale_shape`](). The "Netwrap" and "John Deere CoverEdge" binding types apply only to round bales.

### Field [`hay_compression`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ uncompressed | 2:1 ]</dd>
</dl>


<p>Hay may be mechanically compressed to increase density for transport purposes. This practice is commonplace for export purposes. We are not aware of any compression schemes other than "double compression" at present, so in theory a boolean data type would suffice for this field, but we have cast it as type "enum" to allow for the introduction of other compression ratios in the future.</p>

### Field [`bale_weight_intended`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A positive integer representing the magnitude of the intended bale weight, rounded to the nearest applicable unit, as determined in the baler.</dd>
</dl>

<details>
  <summary>More information</summary>
  
  Express bale weights, whether intended or as assessed, as an average across all bales offered for sale under this product definition. If lack of uniformity would make such an expression misleading, indicate as such using the value "Grower estimate--disparate bales" in the field [`bale_weight_assessment_method`]().

  Systems implementing this standard may wish to validate this field for numerical input and reasonable magnitudes.
  
</details>

### Field [`bale_weight_units`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ kilograms | pounds ]</dd>
</dl>

### Field [`bale_weight_assessment`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A positive integer representing the magnitude of the assessed bale weight, rounded to the nearest applicable unit, as determined by the seller.</dd>
</dl>

<p>Systems implementing this standard may wish to validate this field for numerical input and reasonable magnitudes.</p>

### Field [`bale_weight_assessment_method`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ Truckload average | Explicit weight | Baler target | Grower estimate--uniform bales | Grower estimate--disparate bales ]</dd>
</dl>

### Field [`bale_shape`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ rectangular | round ]</dd>
</dl>

### Field [`bale_dimension_width`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A positive integer value representing the magnitude of the intended bale width, rounded to the nearest applicable unit, as determined in the baler. Applicable to square bales only.</dd>
</dl>

<p>Systems implementing this standard may wish to validate this field for numerical input, reasonable magnitudes, and bale shape.</p>

### Field [`bale_dimension_height`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A positive integer value representing the magnitude of the intended bale height, rounded to the nearest applicable unit, as determined in the baler. Applicable to square bales only.</dd>
</dl>

<p>Systems implementing this standard may wish to validate this field for numerical input, reasonable magnitudes, and bale shape.</p>

### Field [`bale_dimension_length`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A positive integer value representing the magnitude of the intended bale length, rounded to the nearest applicable unit, as determined in the baler. Applicable to square or round bales.</dd>
</dl>

<p>Systems implementing this standard may wish to validate this field for numerical input and reasonable magnitudes.</p>

### Field [`bale_dimension_diameter`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A positive integer value representing the magnitude of the intended bale diameter, rounded to the nearest applicable unit, as determined in the baler. Applicable to round bales only.</dd>
</dl>

<p>Systems implementing this standard may wish to validate this field for numerical input, reasonable magnitudes, and bale shape.</p>

### Field [`bale_dimension_units`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ centimeters | inches ]</dd>
</dl>

### Field [`hay_leafiness`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ Very leafy | Leafy | Slightly stemmy | Stemmy ]</dd>
</dl>

<p>Classification scheme sourced from page 6 of Bates (2018).</p>

### Field [`organoleptic_factor_odor`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ Clean--"crop smell" | Dusty | Moldy | Somewhat sour | Sour | Rotten or otherwise foul ]</dd>
</dl>

<p>Classification scheme adapted from page 6 of Bates (2018).</p>

### Field [`organoleptic_factor_moldy`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`organoleptic_factor_dusty`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`organoleptic_factor_rot`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`foreign_material_weeds`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`foreign_material_burs`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`foreign_material_insects`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>
  
## Hay storage

### Field [`storage_days_fully_exposed`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>A integer value representing how many days this hay has been fully exposed to the elements after baling, whether in the field or otherwise.</dd>
</dl>

### Field [`storage_days_partially_sheltered`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>A integer value representing how many days this hay has been only partially sheltered from the elements after baling, whether in the field or otherwise.</dd>
</dl>

### Field [`storage_days_fully_sheltered`]()
<dl>
  <dt>Data type</dt>
  <dd>int</dd>
  <dt>Valid values</dt>
  <dd>An integer value representing how many days this hay has been fully sheltered from the elements after baling, whether in the field or otherwise.</dd>
</dl>

### Field [`storage_bottom_bales`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ Ground | Pallets | Wood | Concrete | Other ]</dd>
</dl>

# Forage analysis fields

## Sample processing

### Field [`hay_tested`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`hay_sample_date`]()
<dl>
  <dt>Data type</dt>
  <dd>datetime</dd>
  <dt>Valid values</dt>
  <dd>A date in YYYYMMDD format representing the sample date for this hay.</dd>
</dl>

### Field [`hay_sampler_independent`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`hay_sampler_certified`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ true | false | unknown ]</dd>
</dl>

### Field [`hay_sampling_protocol`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ NFTA | other ]</dd>
</dl>

### Field [`hay_testing_laboratory`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>An enumerated value corresponding to a specific laboratory from an open, freely-available database maintained by Fieldgram or another organization or, if self-tested, "Internal lab".</dd>
</dl>

### Field [`hay_testing_method`]()
<dl>
  <dt>Data type</dt>
  <dd>enum</dd>
  <dt>Valid values</dt>
  <dd>= [ Chemical analysis | Near Infrared Reflectance (NIR) spectroscopy | Both chemical analysis and NIR ]</dd>
</dl>

### Field [`hay_testing_date`]()
<dl>
  <dt>Data type</dt>
  <dd>datetime</dd>
  <dt>Valid values</dt>
  <dd>A date in YYYYMMDD format representing the testing date for this hay.</dd>
</dl>

## Base values

### Field [`moisture_content`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding the percentage of water in the sample. This is the complement of dry matter.</dd>
</dl>

### Field [`dry_matter`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding the percentage of dry matter in the sample. This is the complement of moisture content.</dd>
</dl>

## Index values

### Field [`relative_feed_value`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the RFV evaluation of the sample.</dd>
</dl>

## NRC 2001 energy

### Field [`digestible_energy, 1X, Mcal/lb`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the digestible energy of the sample in Mcal/lb.</dd>
</dl>

### Field [`metabolizable_energy, 1X, Mcal/lb`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the metabolized energy of the sample in Mcal/lb.</dd>
</dl>

### Field [`net_energy_lactation, 3X, Mcal/lb`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the net energy of lactation of the sample in Mcal/lb.</dd>
</dl>

### Field [`net_energy_maintenance, 3X, Mcal/lb`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the net energy of maintenance of the sample in Mcal/lb.</dd>
</dl>

### Field [`net_energy_gain, 3X, Mcal/lb`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the net energy gain of the sample in Mcal/lb.</dd>
</dl>

### Field [`digestible_energy, 1X, Mcal/kg`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the digestible energy of the sample in Mcal/kg.</dd>
</dl>

### Field [`metabolizable_energy, 1X, Mcal/kg`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the metabolized energy of the sample in Mcal/kg.</dd>
</dl>

### Field [`net_energy_lactation, 3X, Mcal/kg`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the net energy of lactation of the sample in Mcal/kg.</dd>
</dl>

### Field [`net_energy_maintenance, 3X, Mcal/kg`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the net energy of maintenance of the sample in Mcal/kg.</dd>
</dl>

### Field [`net_energy_gain, 3X, Mcal/kg`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the net energy gain of the sample in Mcal/kg.</dd>
</dl>

### Field [`TDN1X`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the Total Digestible Nutrients (TDN) at 1X maintenance.</dd>
</dl>

## Protein and protein fractions

### Field [`crude_protein`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the crude protein content of the sample in percentage terms, on a dry-matter basis.</dd>
</dl>

### Field [`available_protein`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the available protein content of the sample in percentage terms, on a dry-matter basis.</dd>
</dl>

### Field [`acid_detergent_insoluble_crude_protein`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the acid detergent insoluble crude protein content of the sample in percentage terms.</dd>
</dl>

### Field [`adjusted_crude_protein`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the adjusted crude protein content of the sample in percentage terms.</dd>
</dl>

### Field [`soluble_protein_%_cp`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the soluble crude protein content of the sample in percentage terms.</dd>
</dl>

  ### Field [`degradable_protein_%_cp`]()
  <dl>
    <dt>Data type</dt>
    <dd>float</dd>
    <dt>Valid values</dt>
    <dd>A value corresponding to the degadable crude protein content of the sample in percentage terms.</dd>
  </dl>

### Field [`neutral_detergent_insoluble_crude_protein`]()
<dl>
  <dt>Data type</dt>
  <dd>float</dd>
  <dt>Valid values</dt>
  <dd>A value corresponding to the neutral detergent insoluble crude protein content of the sample in percentage terms.</dd>
</dl>

## Amino acids

### Field [`lysine`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`methionine`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

## Carbohydrates

### Field [`acid_detergent_fiber`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`neutral_detergent_fiber`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`lignin`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`non-fiber_carbohydrates`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`starch`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`water_soluble_carbohydrates`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`ethanol_soluble_carbohydrates`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`in_vitro_true_digestibility_30hr, % of DM`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`neutral_detergent_fiber_digestibility_30hr, % of NDF`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

## Fat

### Field [`crude_fat`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`total_fatty_acids`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`rumen_unsaturated_fatty_acid_load`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

## Energy and digestibility

### Field [`total_digestible_nutrients`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`net_energy_lactation, Mcal/lb`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`net_energy_maintenance, Mcal/lb`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`net_energy_gain, Mcal/lb`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`kd, %/hr`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`horse_digestible_energy, Mcal/lb`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

## Minerals

### Field [`ash`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`calcium`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`phosphorous`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`magnesium`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`potassium`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`sulfur`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`chloride_ion`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`iron_PPM`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`zinc_PPM`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`copper_PPM`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`manganese_PPM`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

### Field [`molybdenum_PPM`]()
<dl>
  <dt>Data type</dt>
  <dd></dd>
  <dt>Valid values</dt>
  <dd></dd>
</dl>

# References

302 KAR 37:010. [Standard Hay Grading Program for the State of Kentucky](https://apps.legislature.ky.gov/law/kar/302/037/010.pdf) [PDF]. Retrieved June 19, 2018.

Baker, R. and S. Ball. 2011. [Variations in Alfalfa Hay Grading](http://lubbock.tamu.edu/files/2011/10/nmsugrading_10.pdf) [PDF]. New Mexico State University Cooperative Extension Service, Guide A-329. Retrieved June 19, 2018.

Ball, D.M., M. Collins, G.D. Lacefield, N.P. Martin, D.A. Mertens, K.E. Olson, D.H. Putnam, D.J. Undersander, and M.W. Wolf. 2001. [Understanding Forage Quality](http://pss.uvm.edu/pdpforage/Materials/ForageQuality/Understanding_Forage_Quality_Ball.pdf) [PDF]. American Farm Bureau Federation Publication 1-01, Park Ridge, IL, via National Forage Testing Association. Retrieved June 19, 2018.

Bates, G. [High Quality Hay Production](https://shelbycountytn.gov/DocumentCenter/View/1183/High-Quality-Hay-Production?bidId=) [PDF]. University of Tennessee Agricultural Extension Service Publication SP 437-A. Retrieved June 19, 2018.

Canadian Food Inspection Agency. 2013. D-03-14: [Canadian Hay Certification Program to certify hay for export](https://inspection.canada.ca/plant-health/invasive-species/directives/grains-and-field-crops/d-03-14/eng/1323829800901/1323829873124). Retrieved June 19, 2018.

Carolina Farm Stewardship Association. [Organic and Non-GMO Feed and Hay Sources Finder](https://www.carolinafarmstewards.org/organic-and-non-gmo-feed-and-hay-sources-for-the-carolinas/). Retrieved June 19, 2018.

Corriher, V., T. Provin, and L. Redmon. 2010. [Hay Production in Texas](http://soiltesting.tamu.edu/publications/E-273.pdf) [PDF]. Texas A&M AgriLife Extension, E-273. Retrieved June 19, 2018.

Corriher, V. and L. Redmon. 2009. [Bermudagrass Varieties, Hybrids and Blends for Texas](http://publications.tamu.edu/FORAGE/PUB_forage_Bermudagrass%20Varieties.pdf) [PDF]. Texas A&M AgriLife Extension, SCS-2009-11. Retrieved June 19, 2018.

Guerrero, J. 2001. [Marketing Standards for Southern California Grass Export Hay](https://alfalfa.ucdavis.edu/+symposium/proceedings/2001/01-207.pdf) [PDF]. University of California Cooperative Extension. Retrieved June 19, 2018.

Lawrence, L. and R. Coleman. 2000. [Choosing Hay for Horses](http://www2.ca.uky.edu/agcomm/pubs/id/id146/id146.pdf) [PDF]. University of Kentucky Cooperative Extension Service, ID-146. Retrieved June 19, 2018.

Marsalis, M., G. Hagevoort, and L. Lauriault. 2009. [Hay Quality, Sampling, and Testing](https://aces.nmsu.edu/pubs/_circulars/CR641/). New Mexico State University Cooperative Extension Service, Circular 641. Retrieved June 19, 2018.

National Alfalfa Alliance. [Alfalfa: The High Quality Hay for Horses](http://www.alfalfa.org/pdf/Alfalfa%20for%20Horses%20(low%20res).pdf) [PDF]. Retrieved June 19, 2018.

Putnam, D. 2010. [Changing Forage Quality Testing for Alfalfa Hay Markets](https://alfalfa.ucdavis.edu/+symposium/2010/files/talks/CAS24_PutnamQualityMarkets.pdf) [PDF]. University of California Department of Plant Sciences (UC Davis). Retrieved June 19, 2018.

Putnam, D. 2003. [Recommended Principles for Proper Hay Sampling](https://wolfe.ca.uky.edu/files/principals_for_proper_hay_testing.pdf) [PDF]. University of California, Davis, via National Forage Testing Association. Retrieved June 19, 2018.

Provin, T. and J. Pitt. 2002. [Sampling Hay Bales and Pastures for Forage Analysis](http://ward.agrilife.org/files/2011/07/tmppdfs_45776-e148.pdf) [PDF]. Texas A&M AgriLife Extension, E-148. Retrieved June 19, 2018.


