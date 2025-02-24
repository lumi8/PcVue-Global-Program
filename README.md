# PcVue-Global-Program
The idea is to create and share the best global SCADA Basic program

## [SCADA Basic programming guidelines](https://www.pcvue.com/ProductHelp/PcVue/en/Content/Scripting_SCADABasic/Concepts/Some_Guidelines.php)

## [The Global Program](https://www.pcvue.com/ProductHelp/PcVue/en/Content/Scripting_SCADABasic/Concepts/Global_Program.php)

## Formatting conventions

### Indentation

* Use spaces, not tabs.
* Each level of indentation must be 4 spaces.

### Blank lines

* Separate items and statements by either zero or one blank lines

### Statements

* Put a space on both sides of the = . Don't put a space before the semicolon:
  *  ```flag = 1;```

### Declarations

* Use a prefix to indicate the type of the variables:
```
Dim iIndex As Integer;
Dim dCounter As Double;
Dim sName As str;
```

* Use CamelCase for variable names and function names:
```
sub ComboGetText()

Dim sCbxText As Str;
Dim sCbxData As Str;
Dim lRet As Long;
Dim lCount As Long;
Dim sCurrentMimic as str;

G_Trace("Control, ComboGetText");
sCurrentMimic = Window("CURRENTNAME");
Print("Current mimic : ", sCurrentMimic);
lRet = ComboBox("GETSELECTEDINDEX", sCurrentMimic, "", "AIComboBox1"); 

sCbxText = ComboBox("GETTEXT", sCurrentMimic, "", "AIComboBox1", lRet); 
sCbxData = ComboBox("GETUSERDATA", sCurrentMimic, "", "AIComboBox1", lRet); 
lCount = ComboBox("COUNT", sCurrentMimic, "", "AIComboBox1"); 

@combocontroldata = sCbxData;
@combocontroltext = sCbxText;
@combocount = Toc(lCount);

ComboBox("SETSELECTEDINDEX", sCurrentMimic, "", "AIComboBox1", lRet); 

end sub
```

* Use UPPER_CASE to declare constants:
```
Const MY_CONSTANT = 23;
```

* Add a prefix G_ before variable name in global program:
```
Dim G_iCyclic10sec As Integer;
Dim G_sSeedOfficeStandard As Str;
Dim G_sSeedOfficeOpenSpace As Str;
Dim G_sSeedOfficeMeetingRoom As Str;

Const G_MAX_DATASET = 100;
Const G_MAX_BUILDING = 1;
Const G_MAX_FLOOR = 10;
Const G_MAX_OFFICE = 5;

Dim G_iTraceEnable As Integer;
Dim G_sProjectPath As Str;
Dim G_siNbDesk As Single;
```
### Items

* External declaration must be done on top of the file. They must be ordered alphabetically.
* Use UPPERCASE for instruction’s modes:
```
Trace("LOG","Message");
AlarmDisplay("FILTER", sWindow, sBranch, sIdentity, sFilter);
sCurrentMimic = Window("CURRENTNAME");
```
* Add a space after a comma:
```
AlarmDisplay("FILTER", sWindow, sBranch, sIdentity, sFilter);
```

