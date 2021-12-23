---
layout: default
title: Field Test
nav_order: 4
---
# Forage analysis fields

<details>
  
  <summary>Click to expand</summary>

## Sample processing

<details>
  
  <summary>Click to expand</summary>

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
  
</details>

## Base values

<details>
  
  <summary>Click to expand</summary>

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

</details>

## Index values
  
<details>
  
  <summary>Click to expand</summary>

  ### Field [`relative_feed_value`]()

  <dl>
    <dt>Data type</dt>
    <dd>float</dd>
    <dt>Valid values</dt>
    <dd>A value corresponding to the RFV evaluation of the sample.</dd>
  </dl>

</details>

## NRC 2001 energy

<details>
  
  <summary>Click to expand</summary>

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
  
</details>

## Protein and protein fractions

<details>
  
  <summary>Click to expand</summary>

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
  
</details>

## Amino acids

<details>
  
  <summary>Click to expand</summary>

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
  
</details>

## Carbohydrates

<details>
  
  <summary>Click to expand</summary>

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
  
</details>

## Fat

<details>
  
  <summary>Click to expand</summary>

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
  
</details>

## Energy and digestibility

<details>
  
  <summary>Click to expand</summary>

  ### Field [`total_digestible_nutrients`]()
  
  <dl>
    <dt>Data type</dt>
    <dd></dd>
    <dt>Valid values</dt>
    <dd></dd>
  </dl>

  ### Field [`net_energy_lactation, Mcal/Lb`]()
  
  <dl>
    <dt>Data type</dt>
    <dd></dd>
    <dt>Valid values</dt>
    <dd></dd>
  </dl>

  ### Field [`net_energy_maintenance, Mcal/Lb`]()
  
  <dl>
    <dt>Data type</dt>
    <dd></dd>
    <dt>Valid values</dt>
    <dd></dd>
  </dl>

  ### Field [`net_energy_gain, Mcal/Lb`]()
  
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

  ### Field [`horse_digestible_energy, Mcal/Lb`]()
  
  <dl>
    <dt>Data type</dt>
    <dd></dd>
    <dt>Valid values</dt>
    <dd></dd>
  </dl>
  
</details>

## Minerals

<details>
  
  <summary>Click to expand</summary>

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
  
</details>

</details>
