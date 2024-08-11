### pageSection()
 <hr>
  
 This function retrieves either a section items based on the provided alias.
  
 ##### Parameters
 - `$alias` : The alias of the section item(s) to retrieve.
 - `$sectionData` (optional)  : An array or collection of section items.


 ##### Return Value
  - The HTML content of the section item(s).
  
 ##### Example Usage
   ```
  
  {! pageSection('our-brands') !}

  //or
  {! pageSection('our-brands', $sectionData) !}
   
   ```