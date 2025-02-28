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
Dim i_index As Integer;
Dim l_handle As Long;
Dim ll_result As LongLong;
Dim si_nb_room As Single;
Dim d_counter As Double;
Dim s_name As Str;
```

* Use UPPER_CASE to declare constants:
```
Const MY_CONSTANT = 23;
```

* Use snake_case for variable and function names:
```
Sub combo_get_text()

Dim s_cbx_text As Str;
Dim s_cbx_data As Str;
Dim l_ret As Long;
Dim l_count As Long;
Dim s_current_mimic as str;

G_trace("Control, combo_get_text");
s_current_mimic = Window("CURRENTNAME");
Print("Current mimic : ", s_current_mimic);
l_ret = ComboBox("GETSELECTEDINDEX", s_current_mimic, "", "AIComboBox1"); 

s_cbx_text = ComboBox("GETTEXT", s_current_mimic, "", "AIComboBox1", l_ret); 
s_cbx_data = ComboBox("GETUSERDATA", s_current_mimic, "", "AIComboBox1", l_ret); 
l_count = ComboBox("COUNT", s_current_mimic, "", "AIComboBox1"); 

@combocontroldata = s_cbx_data;
@combocontroltext = s_cbx_text;
@combocount = Toc(l_count);

ComboBox("SETSELECTEDINDEX", s_current_mimic, "", "AIComboBox1", l_ret); 

End Sub
```

* Add a prefix G_ before variables and functions in global program:
```
Dim G_i_cyclic_10_sec As Integer;
Dim G_s_seed_office_standard As Str;

Const G_MAX_DATASET = 100;
Const G_MAX_BUILDING = 1;
Const G_MAX_FLOOR = 10;
Const G_MAX_OFFICE = 5;

Dim G_i_trace_enable As Integer;
Dim G_si_nb_desk As Single;

Sub G_trace(trace)
'…
End Sub
```
### Items

* External declaration must be done on top of the file. They must be ordered alphabetically.
* Use UPPERCASE for instruction’s modes:
```
Trace("LOG","Message");
AlarmDisplay("FILTER", s_window, s_branch, s_identity, s_filter);
s_current_mimic = Window("CURRENTNAME");
```
* Add a space after a comma:
```
AlarmDisplay("FILTER", s_window, s_branch, s_identity, s_filter);
```

