# mariuszmaciaszek.github.io

20221222 js

```
//*******************************************************************************
function AADD(t,v){
//*******************************************************************************
//AADD()
//Add a new element to the end of an array
//Syntax
//    AADD(<aTarget>, <expValue>) --> Value
//Arguments
//    <aTarget> is the array to which a new element is to be added.
//    <expValue> is the value assigned to the new element.
//Returns
//    AADD() evaluates <expValue> and returns its value.  If <expValue> is not
//    specified, AADD() returns NIL.
 if( v === undefined ) v = NIL;
 t[LEN(t)+1] = v;
 return v;
};
//*******************************************************************************
function AADD_testy(){
//*******************************************************************************
 debugger;
 
 var T = [];
 alert(LEN(T));
 alert(VALTYPE(T));
 AADD(T,123);
 alert(LEN(T));
 alert(VALTYPE(T));
 
}
```

```
//*******************************************************************************
function ABS( exp_ ){
//*******************************************************************************
//Return the absolute value of a numeric expression.
 return Math.abs(exp_);
}
```

```
//*******************************************************************************
function AFILL(t,v,start_,count_){
//*******************************************************************************
//AFILL()
//Fill an array with a specified value
//Syntax
//    AFILL(<aTarget>, <expValue>,
//       [<nStart>], [<nCount>]) --> aTarget
//
//Arguments
//
//    <aTarget> is the array to be filled.
//
//    <expValue> is the value to be placed in each array element.  It can
//    be an expression of any valid data type.
//
//    <nStart> is the position of the first element to be filled.  If this
//    argument is omitted, the default value is one.
//
//    <nCount> is the number of elements to be filled starting with
//    element <nStart>.  If this argument is omitted, elements are filled from
//    the starting element position to the end of the array.
//
//Returns
//
//    AFILL() returns a reference to <aTarget>.
//
//Description
//
//    AFILL() is an array function that fills the specified array with a
//    single value of any data type (including an array, code block, or NIL)
//    by assigning <expValue> to each array element in the specified range.
//
//    Warning!  AFILL() cannot be used to fill multidimensional arrays.
//    CA-Clipper implements multidimensional arrays by nesting arrays within
//    other arrays.  Using AFILL() with a multidimensional array will
//    overwrite subarrays used for the other dimensions of the array.
//
//Examples
//
//       This example, creates a three-element array.  The array is
//       then filled with the logical value, (.F.).  Finally, elements in
//       positions two and three are assigned the new value of true (.T.):
//
//       LOCAL aLogic[3]
//       // Result: aLogic is { NIL, NIL, NIL }
//
//       AFILL(aLogic, .F.)
//       // Result: aLogic is { .F., .F., .F. }
//
//       AFILL(aLogic, .T., 2, 2)
//       // Result: aLogic is { .F., .T., .T. }

 if( start_ === undefined ) start_ = 1;
 if( count_ === undefined ) count_ = LEN(t);
 
 for( var f = start_ ; f <= MIN(start_+count_-1,LEN(t)) ; f++ ) t[f] = v;

 return t;
}

//*******************************************************************************
function AFILL_testy(){
//*******************************************************************************
 debugger;
 
 var A = [];//{}
 
 ASIZE(A,3);//{ NIL, NIL, NIL }
 
 AFILL(A,false);//{ .F., .F., .F. }
 
 AFILL(A,true,2,2);//{ .F., .T., .T. }
 
}
```

```
//*******************************************************************************
function ALERT(m,o){
//*******************************************************************************
//ALERT()
//Display a simple modal dialog box
//Syntax
//    ALERT( <cMessage>, [<aOptions>] ) --> nChoice

 if( EMPTY(o) ) o = [0,'OK'];

 var a = '';
 a += m + '\n\n';
 
 var f;
 for( f = 1 ; f <= LEN(o) ; f++ ){
  a += '[' + f + '-' + o[f] + ']   ';
 };
 
 //      InputBox( prompt , title  , msg, xpos, ypos){
 var p = InputBox( a      , 'ALERT', '1')
 p = parseInt(p);
 if( isNaN(p) ) p = 0;
 
 return p;
}
```

```
//*******************************************************************************
function ALLTRIM( tekst_ ) {
//*******************************************************************************
 if( tekst_ == null ) return '';
 return tekst_.replace(/^\s+|\s+$/g,"");
};
//*******************************************************************************
function ALLTRIM_testy()
{
    debugger;
    if( ALLTRIM( SPACE(10) + "string" + SPACE(10) ) == "string" ) {'ok'} else debugger;
    if( ALLTRIM( CHR(9) + "string" + CHR(9) )       == "string" ) {'ok'} else debugger;
    if( ALLTRIM( CHR(9) + " " + CHR(9) + " " + "string" + CHR(9) + " " + CHR(9) + " " ) == "string" ) {'ok'} else debugger;
    if( ALLTRIM( " " + CHR(9) + " " + CHR(9) + "string" + " " + CHR(9) + " " + CHR(9) ) == "string" ) {'ok'} else debugger;
}
```

```
//*******************************************************************************
function ALTD(){
//*******************************************************************************
 debugger;
 alert("debugger");
}
```




20221221
c#

```
//odczyt aktualnego katalogu
string path = Directory.GetCurrentDirectory();
```

```
//Odczyt daty pliku z tabeli.
var _dataPliku = new DateTime();
try
{ 
  var _r = db.Tabela.FirstOrDefault();
  _dataPliku = _r.DATA_PLIKU;
}
catch
{
}
```

```
//Odczyt daty pliku
var _nazwaPliku = "test.xlsx";
var _dataPliku = new DateTime();
FileInfo _file = new FileInfo(_nazwaPliku);
_dataPliku = _file.LastWriteTime;
```


```
//Porównywanie dat.
if( _dataPliku.CompareTo(_dataPliku) == 0 )
{
  //daty są takie same
}
```


```
//Usunięcie wszystkich wierszy z tabeli
db.Tabela.RemoveRange(db.Tabela);
db.SaveChanges();
```

```
//Import danych z excela do tabeli
var _nazwaPliku = "test.xlsx";
var _wb = new XLWorkbook(_nazwaPliku);
var _ws = _wb.Worksheet(1);
var firstCell = _ws.FirstCellUsed();
var lastCell = _ws.LastCellUsed();
var range = _ws.Range(firstCell.Address, lastCell.Address);
var table = range.CreateTable();//Można użyć też range.AsTable()
var _id = 0;
foreach(var row in table.DataRange.Rows())
{
  _id++;
  //Dodanie nowego rekordu do tabeli.
  var _Tabela = new DbTabela();
  _Tabela.T_ID = _id;
  _Tabela.T_KOLUMNA1 = row.Field("kolumna1").GetString();
  _Tabela.T_KOLUMNA2 = row.Field("kolumna2").GetString();
  _Tabela.T_KOLUMNA3 = row.Field("kolumna3").GetString();
  db.Tabela.Add(_TAbela);
  db.SaveChanges();
}
```


