# Unicode-aware-controls
Display Unicode text in PROMPT, STRING, CHECK, RADIO controls

### Overview
This set of classes allows to display Unicode text in screen controls (PROMPT, STRING, CHECK, RADIO).  
![Unicode demo](https://github.com/mikeduglas/Unicode-aware-controls/blob/master/UnicodeDemo.jpg?raw=true)  

### How it works
To simplify the job there is TUnicodeControlMgr class, you just call AddControl method to enable Unicode support for a control:
```
xMgr    TUnicodeControlMgr  !- unicode control manager
  CODE
  xMgr.AddControl(?PROMPT1)
  xMgr.AddControl(?CHECK1)
  xMgr.AddControl(?RADIO1)
```
To change a text displayed in a control you still use PROP:Text property and pass Unicode string in UTF16 format:
```
  PROMPT1{PROP:Text} = '<0FFh,0FEh><39h,26h><0Fh,0FEh><0Dh,00h><0Ah,00h><39h,26h><0Fh,0FEh><00h,00h>'
```
Well, it looks confusing enough, but there are 2 soltions.
1. I have an utility which can convert unicode file to its Clarion representation. Thus you just open Unicode file and get encoded string whic
can be copied and pasted right into the code.
2. There is TResourceManagerW class which lets you read Unicode INI files from disk or program resource. For example you have this INI:
```
[Unicode]
Info_1=This page demonstrates Unicode in screen controls: prompts, strings, checkboxes and radios.
Info_2=Эта страница демонстрирует Юникод в элементах управления экрана: подсказках, строках, флажках и радио.
Info_3=本页在屏幕控件中演示Unicode：提示，字符串，复选框和单选.
Info_4=Αυτή η σελίδα εμφανίζει το Unicode στα χειριστήρια οθόνης: προτροπές, συμβολοσειρές, πλαίσια ελέγχου και ραδιόφωνα.
```
then to display say Info_2 value in ?PROMPT1 you write
```
?PROMPT1{PROP:Text} = iniMgr.ReadKey('Main', 'Info_2', 'Value not found.')
```
so ReadKey reads a key value from [Main] section.  

### Demo program
The demo can be downloaded [here](https://www.dropbox.com/s/5d6cabic0ob9k4d/UnicodeDemo.zip?dl=0).

### Requirements
- CW6 and newer
- ABC and Clarion template chain
- No extra libraries

### Price
$200

### Contacts
mikeduglas@yandex.ru

