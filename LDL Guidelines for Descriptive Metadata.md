# LDL Guidelines for Descriptive Metadata
text here about this document and the why it exists 

## General Guidelines 
The following guidelines apply to all descriptive metadata for the LDL

* For any field that is not applicable, leave blank; do not enter “N/A” or “None” or equivalent.
* Ending punctuation is not required for field content and is only recommended in fields where complete sentences are used (e.g. notes, description).
* For purposes of distinguishing between formally published and unpublished materials, do not consider publication in the LDL as formal publication. “Formally published” in these guidelines refers to formal publication of the original materials, rather than the digital representation.
* When in doubt, adherence to RDA standards is advised.

### General Guidelines for Spreadsheets 
Spreadsheets are used for bulk uploads of most content types. The following guidelines are specific to the creation of well-formed descriptive metadata spreadsheets.

* When saving, name your spreadsheet file using the intended collection namespace-PID (e.g. “hnoc-delcroix.xlsx”)
* One line in the spreadsheet equates to one MODS record.
 * Compound objects should have one line for the parent level item and one line for each of the child level items.
* Where multiple values are appropriate in a repeatable field (names, subject terms, languages, etc.), separate each value with a semicolon followed by a space.
* If a custom field is needed for a collection, a column may be added to the spreadsheet or an existing column header may be modified. Please use colored highlighting in the spreadsheet to mark that field for specialized mapping.
 * To aid in mapping efforts, preferred formatting for headers is: ‘MODS Element (Desired Display Label)’ or ‘MODS Element [Type Attribute Value] (Desired Display Label)’. For example:
  * **Identifier** (Accession Number)
  * **Note** [biographical/historical] (Biographical Note)
 * If you don’t know the element name or attribute value, you may enter only the desired display label, and LSU staff will collaborate with you to work out the best MODS mapping.
* Do not make modifications to any sheets except the first. (The others are for storage of controlled vocabulary terms.)

#### Guidelines for Structural Data in Spreadsheets

**Identifier**. Enter a sequential item number per record, beginning at 1 (such that each line is numbered in order, 1, 2, 3, 4…).

**Child**. For compound objects, enter a secondary sequential item number, beginning at 01, per child item (such that each compound object has numbered children, 01, 02, 03…). (Leave blank if simple.)

**Directory**. For compound objects, enter the folder name of the parent item in the directory. (Leave blank if simple.)

**File Name**. Enter the file name, including the file extension, for the object described in the record. (Leave blank for compound parent.)

### General Guideline for Web Interface 
* For any field group where you click “Add” to add a new element set, note that you aren’t automatically sent to the new tab when it is created. Remember to click the new tab rather than overwrite the previous tab’s information.
* The difference between “Tabs” and “Tags”
* For any field group including a “Display Label” field, the preferred text with its capitalization should be included, but not delimiters such as colons. 

## Descriptive Metadata Guidelines 



