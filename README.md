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


```
//*******************************************************************************
function ARRAY(d){
//*******************************************************************************
//ARRAY()
//Create an uninitialized array of specified length
//Syntax
//    ARRAY(<nElements> [, <nElements>...]) aArray
//Arguments
//    <nElements> is the number of elements in the specified dimension.
//    The maximum number of elements in a dimension is 4096.  Arrays in
//    CA-Clipper can have an unlimited number of dimensions.
//Returns
//    ARRAY() returns an array of specified dimensions.
//
//todo: wielowymiarowe tablice
 var r = [];
 if( d === undefined ) return r;
 return ASIZE(r,d);
}
```

```
//*******************************************************************************
function ASIZE(t,l){
//*******************************************************************************
//ASIZE()
//Grow or shrink an array
//Syntax
//    ASIZE(<aTarget>, <nLength>) --> aTarget
//Arguments
//    <aTarget> is the array to grow or shrink.
//    <nLength> is the new size of the array.
//Returns
//    ASIZE() returns a reference to the target array, <aTarget>.
 
 if( l == LEN(t) ) return t;
 
 if( l <  LEN(t) ){
  //Obcinanie elementów.
  while( l < LEN(t) ) t.pop();
  return t;
 };
 
 //Dodawanie pustych elementów
 while( l > LEN(t) ) t.push(NIL);
 return t;
};
//*******************************************************************************
function ASIZE_testy(){
//*******************************************************************************
 debugger;
 var t = [];
 AADD(t,1);alert(LEN(t));
 AADD(t,2);alert(LEN(t));
 AADD(t,3);alert(LEN(t));
 ASIZE(t,2);alert(LEN(t));
 ASIZE(t,1);alert(LEN(t));
 ASIZE(t,0);alert(LEN(t));
 ASIZE(t,1);alert(LEN(t));
 ASIZE(t,2);alert(LEN(t));
}
```


```
//*******************************************************************************
function AT( search_ , target_ ){
//*******************************************************************************
//Return the position of a substring within a character string
//Syntax
//
//    AT(<cSearch>, <cTarget>) -> nPosition
//
 return ( target_.indexOf(search_) + 1 );
}
```


```
//*******************************************************************************
function CHR(n_) {
//*******************************************************************************
 return String.fromCharCode(n_);
}
```

```
//*******************************************************************************
function CTOD(s,format_) {
//*******************************************************************************
//Convert a date string to a date value
//Syntax
//    CTOD(<cDate>) --> dDate
//Arguments
//    <cDate> is a character string consisting of numbers representing the
//    month, day, and year separated by any character other than a number.
//    The month, day, and year digits must be specified in accordance with the
//    SET DATE format.  If the century digits are not specified, the century
//    is determined by the rules of SET EPOCH.
//Returns
//    CTOD() returns a date value.  If <cDate> is not a valid date, CTOD()
//    returns an empty date.
//Description
//    CTOD() is a character conversion function that converts a character
//    string to a date.  To initialize an empty date for date entry, specify
//    <cDate> as a null string (""), SPACE(8), or "  /  /  ".
//    CTOD() is used whenever you need a literal date value.  Some examples
//    are:
//    -  Initializing a variable to a date value
//    -  Specifying a literal date string as an argument of a RANGE
//       clause of @...GET
//    -  Specifying a literal date string in order to perform date
//       arithmetic
//    -  Comparing the result of a date expression to a literal date
//       string
//    -  REPLACEing a date field with a literal date string
//    -  REPLACEing a date field with a literal date string
//    CTOD() is the inverse of DTOC() which converts a date value to a
//    character string in the format specified by SET DATE and SET CENTURY.
//    DTOS() also converts a date value to a character string in the form
//    yyyymmdd.
//
 if( s == '' ) return null;
 if( format_ == undefined ) format_ = SET(_SET_DATEFORMAT);
 

 //...................
 //DD-MM-YYYY
 //0123456789
 //...................
 if( format_ == 'DD-MM-YYYY' ){
  var year_  = parseInt( s.substr(6,4) , 10 );
  var month_ = parseInt( s.substr(3,2) , 10 ) -1; //0-styczeń, 1-luty ... 11-grudzień
  var day_   = parseInt( s.substr(0,2) , 10 );
  var date_  = new Date( year_ , month_ , day_ );
  if( !( date_.getDate()     == day_   ) ) return null; //Niezgodny dzień
  if( !( date_.getMonth()    == month_ ) ) return null; //Niezgodny miesiąc
  if( !( date_.getFullYear() == year_  ) ) return null; //Niezgodny rok
  return date_;
 };
 

 alert('ERROR 20130124_1417 Do implementacji, s='+s+' format_='+format_ );
 return new Date(s);
}
```


```
//************************************************************
function CURDIR(d){
//************************************************************
//CURDIR()
//Return the current DOS directory
//Syntax
//
//    CURDIR([<cDrivespec>]) --> cDirectory
//
//Arguments
//
//    <cDrivespec> specifies the letter of the disk drive to query.  If
//    not specified, the default is the current DOS drive.
//
//Returns
//
//    CURDIR() returns the current DOS directory of the drive specified by
//    <cDrivespec> as a character string without either leading or trailing
//    backslash (\) characters.
//
//    If an error occurs, or the current directory of the specified drive is
//    the root directory, CURDIR() returns a null string ("").
//
//Description
//
//    CURDIR() is an environment function that gives you the name of the
//    current DOS directory, ignoring the SET DEFAULT and SET PATH settings.
//
//Examples
//
//    -  These examples illustrate various CURDIR() results:
//
//       ? CURDIR("E:")     // Result: null string--root directory
//       ? CURDIR("C")      // Result: CLIP53\SOURCE
//       ? CURDIR("C:")     // Result: CLIP53\SOURCE
//       ? CURDIR()         // Result: null string--root directory
//       ? CURDIR("A")      // Result: null string--drive not ready

 if(!EMPTY(d)) alert('ERROR 20140513_1451 Nieobsługiwany parametr. TODO.');
 
 if( typeof WScript_Shell == 'undefined' ) WScript_Shell = new ActiveXObject("WScript.Shell");

 var s = WScript_Shell.CurrentDirectory;//s:\zycie
 s = s.toUpperCase();
 s = s.split(':\\')[1];
 return s
}
```


```
//************************************************************
function DATE(){
//************************************************************
 return new Date;
}
```


```
//*******************************************************************************
function DATE_add_days( date_ , days_ ){
//*******************************************************************************
//Do daty dodaje ilość dni.
//Przykład:
//   var data_ = DATE_add_days( DATE() , 10 );//Do daty dodaje ilość dni.
//
 var d = new Date(date_);
 d.setDate(   d.getDate() + days_   );
 return d;
};
//*******************************************************************************
function DATE_add_days_testy() {
//*******************************************************************************
 debugger;
 var date_ = STOD('20130208');
 if( DTOS(DATE_add_days(date_,-8)) == '20130131' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,-7)) == '20130201' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,-6)) == '20130202' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,-5)) == '20130203' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,-4)) == '20130204' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,-3)) == '20130205' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,-2)) == '20130206' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,-1)) == '20130207' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_, 0)) == '20130208' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_, 1)) == '20130209' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_, 2)) == '20130210' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_, 3)) == '20130211' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_, 4)) == '20130212' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_, 5)) == '20130213' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_, 6)) == '20130214' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_, 7)) == '20130215' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_, 8)) == '20130216' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_, 9)) == '20130217' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,10)) == '20130218' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,11)) == '20130219' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,12)) == '20130220' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,13)) == '20130221' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,14)) == '20130222' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,15)) == '20130223' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,16)) == '20130224' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,17)) == '20130225' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,18)) == '20130226' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,19)) == '20130227' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,20)) == '20130228' ) {'ok'} else debugger;
 if( DTOS(DATE_add_days(date_,21)) == '20130301' ) {'ok'} else debugger;
}
```


```
//************************************************************
function DAY(data_) {
//************************************************************
//Return the day of the month as a numeric value
//Syntax
//    DAY(<dDate>) --> nDay
//Arguments
//    <dDate> is a date value to convert.
//Returns
//    DAY() returns a number in the range of zero to 31 as an integer numeric
//    value.  If the month is February, leap years are considered.  If the
//    date argument is February 29 and the year is not a leap year, DAY()
//    returns zero.  If the date argument is empty, DAY() returns zero.
//
 if( typeof(data_)=='date' ) data_ = new Date(data_);//Konwertuje na javascriptowy obiekt Date.
 return ( data_.getDate() );
};
//************************************************************
```



```
//************************************************************
function DTOC(d,f,empt){
//************************************************************
//Convert a date value to a character string.
//Syntax
//    DTOC(<dDate>) --> cDate
//Arguments
//    <dDate> is the date value to convert.

 if( !( empt===undefined) ) if(EMPTY(d)) return empt;

 if( typeof(d)=='date' ){
  //Konwertuje na javascriptowy obiekt Date.
  d = new Date(d);
 };
 
 if( f == undefined ) f = SET(_SET_DATEFORMAT);
 
 
 //----------------------------------
 //DTOC( new Date ,'DD-MM-YYYY')
 //----------------------------------
 if( f ==            'DD-MM-YYYY' ){
  if( EMPTY(d) ) return '  -  -    ';
  var s = '';
  if( d.getDate()     <   10 ) s += '0';
                               s += d.getDate();
                               s += '-';
  var m = d.getMonth() + 1;
  if( m               <   10 ) s += '0';
                               s += m;
                               s += '-';
  if( d.getFullYear() < 1000 ) s += '0';
  if( d.getFullYear() <  100 ) s += '0';
  if( d.getFullYear() <   10 ) s += '0';
                               s += d.getFullYear();
  return s;
 };
 

 //----------------------------------
 //DTOC( new Date ,'YYYY.MM')
 //----------------------------------
 if( f ==            'YYYY.MM' ){
  if( EMPTY(d) ) return '    .  ';
  var s = '';
  if( d.getFullYear() < 1000 ) s += '0';
  if( d.getFullYear() <  100 ) s += '0';
  if( d.getFullYear() <   10 ) s += '0';
                               s += d.getFullYear();
                               s += '.';
  var m = d.getMonth() + 1;
  if( m               <   10 ) s += '0';
                               s += m;
  return s;
 }
}
```


```
//************************************************************
function DTOS(date_) {
//************************************************************
//Convert a date value to a character string formatted as yyyymmdd
//Returns
//    DTOS() returns a character string eight characters long in the format
//    yyyymmdd.  When <dDate> is a null date (CTOD("")), DTOS() returns a
//    string of eight spaces.  The return value is not affected by the current
//    date format.

 if( EMPTY(date_) ) return SPACE(8);

 if( typeof(date_)=='date' ) date_ = new Date(date_);//Konwertuje na javascriptowy obiekt Date.
 
 var s = '';
 if( date_.getFullYear() < 1000 ) s += '0';
 if( date_.getFullYear() <  100 ) s += '0';
 if( date_.getFullYear() <   10 ) s += '0';
                                  s += date_.getFullYear();
 var m = date_.getMonth() + 1;
 if( m                   <   10 ) s += '0';
                                  s += m;
 if( date_.getDate()     <   10 ) s += '0';
                                  s += date_.getDate();
                                  
 return s;
}
```


```
//*******************************************************************************
function EMPTY(x) {
//*******************************************************************************
 
 if( x==null      ) return true;
 if( x==undefined ) return true;
 
 //Data oraclowa.
 if( typeof(x)=='date' ) {
  //Konwertuje na javascriptowy obiekt Date.
  x = new Date(x);
  if( x.getFullYear() == 4712 ) return true; //Mediatorowa pusta data.
  //return Date.parse(x)<0;  //todo: sprawdzić dla innych systemów niż mediator
  return false;
 };

 //Data
 if( x instanceof Date ) return isNaN(Number(x));

 //string 
 if( typeof(x)=='string' ) {
  return ALLTRIM(x)=='';
 };

 //number
 if (typeof(x)=='number' ) {
  if( x==0 ) return true;
  //if (typeof obj == 'number' && isNaN(obj)) return true;
  return false;
 };
 
 if( typeof(x)=='object' ) {
  return false;
 };

 if( typeof(x)=='boolean' ) {
  return !x;
 };
 
 //if (typeof obj == 'undefined' || obj === null || obj === '') return true;
 
 alert('ERROR 20121115_1552 Do implementacji, typeof(x)='+typeof(x)+' x='+x );
};
//*******************************************************************************
function EMPTY_testy() {
//*******************************************************************************
 if( EMPTY(0)==true ) {'ok'} else {debugger};
}
```

```
//*******************************************************************************
function FERASE(f) {
//*******************************************************************************
 //Usuwa plik z dysku.
 //
 //Returns
 //     -1 - niepowodzenie
 //      0 - sukces
 //
 try {
  var fso = new ActiveXObject("Scripting.FileSystemObject");
  fso.DeleteFile(f);
 } catch(e) {
  //ERROR_ = "ERROR 20111012_1216 ";
  //for( var ee in e ) ERROR_ += " " + ee + "=" + e[ee];
  return -1;
 };
 return 0;
}
```


```
var FERROR_static = 0;
//*******************************************************************************
function FERROR() {
//*******************************************************************************
//Test for errors after a binary file operation
//Syntax
//    FERROR() --> nErrorCode
//Returns
//    FERROR() returns the DOS error from the last file operation as an
//    integer numeric value.  If there is no error, FERROR() returns zero.
//
//    FERROR() Return Values
//    Error   Meaning
//    0       Successful
//    2       File not found
//    3       Path not found
//    4       Too many files open
//    5       Access denied
//    6       Invalid handle
//    8       Insufficient memory
//    15      Invalid drive specified
//    19      Attempted to write to a write-protected disk
//    21      Drive not ready
//    23      Data CRC error
//    29      Write fault
//    30      Read fault
//    32      Sharing violation
//    33      Lock Violation
 return FERROR_static;
}
```


```
//*******************************************************************************
function FILE(f){
//*******************************************************************************
//FILE()
//Determine if files exist in the CA-Clipper default directory or path
//Syntax
//    FILE(<cFilespec>) --> lExists
//Arguments
//    <cFilespec> is in the current CA-Clipper default directory and path.
//    It is a standard file specification that can include the wildcard
//    characters * and ? as well as a drive and path reference.  Explicit
//    references to a file must also include an extension.
//Returns
//    FILE() returns true (.T.) if there is a match for any file matching the
//    <cFilespec> pattern; otherwise, it returns false (.F.).
//
 var fso = new ActiveXObject("Scripting.FileSystemObject");
 return fso.FileExists(f);
}
```


```
//*******************************************************************************
function FOPEN(f,m) {
//*******************************************************************************
//Open a binary file
//Syntax
//    FOPEN(<cFile>, [<nMode>]) --> nHandle
//Arguments
//    <cFile> is the name of the file to open, including the path if there
//    is one.
//
//    <nMode> is the requested DOS open mode indicating how the opened
//    file is to be accessed.  The open mode is composed of elements from the
//    two types of modes described in the tables below.  If just the Access
//    Mode is used, the file is opened non-sharable.  The default open mode is
//    zero, which indicates non-sharable and read-only.
//
//    FOPEN() Access Modes
//    Mode    Fileio.ch      Operation
//    0       FO_READ        Open for reading (default)
//    1       FO_WRITE       Open for writing
//    2       FO_READWRITE   Open for reading or writing
//
//    The Sharing Modes determine how other processes may access the file.
//
//    FOPEN() Sharing Modes
//    Mode    Fileio.ch      Operation
//    0       FO_COMPAT      Compatibility mode (default)
//    16      FO_EXCLUSIVE   Exclusive use
//    32      FO_DENYWRITE   Prevent others from writing
//    48      FO_DENYREAD    Prevent others from reading
//    64      FO_DENYNONE    Allow others to read or write
//    64      FO_SHARED      Same as FO_DENYNONE
//
//    The Access Modes in combination (+) with the Sharing modes determine the
//    accessibility of the file in a network environment.
//
//Returns
//
//    FOPEN() returns the file handle of the opened file in the range of zero
//    to 65,535.  If an error occurs, FOPEN() returns -1.
//
//Description
//
//    FOPEN() is a low-level file function that opens an existing binary file
//    for reading and writing, depending on the <nMode> argument.  Whenever
//    there is an open error, use FERROR() to return the DOS error number.
//    For example, if the file does not exist, FOPEN() returns -1 and FERROR()
//    returns 2 to indicate that the file was not found.  See FERROR() for a
//    complete list of error numbers.
//
//    If the specified file is opened successfully, the value returned is the
//    DOS handle for the file.  This value is similar to an alias in the
//    DOS handle for the file.  This value is similar to an alias in the
//    functions.  It is, therefore, important to assign the return value to a
//    variable for later use as in the example below.
//
//    Warning!  This function allows low-level access to DOS files and
//    devices.  It should be used with extreme care and requires a thorough
//    knowledge of the operating system.
//
//Notes
//
//       Accessing files in other directories: FOPEN() does not obey
//       either SET DEFAULT or SET PATH.  Instead, it searches the current DOS
//       directory and path setting unless a path is explicitly stated as part
//       of the <cFile> argument.
 
 FERROR_static = 0;
 
 var h;
 try {
  var ForWriting = 2; 
  fs = new ActiveXObject("Scripting.FileSystemObject");
  h = fs.OpenTextFile( f , ForWriting , false );
 } catch(e) {
  debugger;
  h = -1;
  //FERROR_static = todo!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
 };

 return h;
}
```



```
//-------------------------------------------------------------------------------
function FT_ORIGIN(){
//-------------------------------------------------------------------------------
//Nanforum Toolkit v3.05
//FT_ORIGIN()
//Report the drive, path and filename of the current program
//Syntax
//    FT_ORIGIN() -> cString
//Arguments
//   None
//Returns
//   A string containing the full drive/directory/filename of
//   the currently executing file.
//Description
//   Often users will install multiple copies of application software,
//   especially on networks and in situations where the user is trying
//   to get around a copy protection scheme.
//
//   This function enables you to learn the name and source location
//   of the currently executing file, so that you may take whatever
//   action you need to.
//
//   Requires DOS v3.xx and above.
//
//Examples
//
//   cMyFile := FT_ORIGIN()
//
//   IF cMyFile <> "C:\APPDIR\MYFILE.EXE"
//      ?"Incorrect startup file.  Please remove/rename and start again"
//      QUIT
//   ENDIF
//
//Header File: extend.h
//
//Source: ORIGIN.C
//
//Author: Steve Larsen

 //...............................................
 //HTA
 //...............................................
 //
 if(  typeof(objSOU)=='object'  ){
  var a = objSOU.commandLine;//'"S:\programy\przetw\przetw.01z\sou.hta" "@@alert(123);window.close();"'
  var b = a.split('"');
  return b[1];
 };
 
 throw 'ERROR 20140303_1503 FT_ORIGIN problem z określeniem aplikacji.';
};
//-------------------------------------------------------------------------------
function FT_ORIGIN_testy(){
//-------------------------------------------------------------------------------
 debugger;
 alert(FT_ORIGIN());
}
```


```
//*******************************************************************************
function GETENV(n) {
//*******************************************************************************
//Retrieve the contents of a DOS environment variable
//Syntax
//    GETENV(<cEnvironmentVariable>) --> cString
//Arguments
//    <cEnvironmentVariable> is the name of the DOS environment variable.
//    When specifying this argument, you can use any combination of uppercase
//    and lowercase letters; GETENV() is not case-sensitive.
//Returns
//    GETENV() returns the contents of the specified DOS environment variable
//    as a character string.  If the variable cannot be found, GETENV()
//    returns a null string ("").
//Description
//    GETENV() is an environment function that lets you retrieve information
//    from the DOS environment into an application program.  Typically, this
//    is configuration information, including path names, that gives the
//    location of files (database, index, label, or reports).  This function
//    is particularly useful for network environments.
//Notes
//    Empty return value: If you are certain that an environment
//    variable exists and yet GETENV() always returns a null string (""),
//    be sure there are no spaces between the environment variable name and
//    the first character of the string assigned to it in the DOS SET
//    command.
//    Compatibility: In previous releases of CA-Clipper, the
//    function was called GETE().  This abbreviated form of GETENV() is
//    still operational.
//
 var shell_ = new ActiveXObject("WScript.Shell");
 var env_   = shell_.Environment("PROCESS");
 var v      = env_(n);
 return v;
}
```



```
//*******************************************************************************
function IF( lCondition , expTrue , expFalse ) {
//*******************************************************************************
 if( lCondition ) return expTrue;
 return expFalse;
}
```



```
//*******************************************************************************
function INT(exp_){
//*******************************************************************************
//INT()
//Convert a numeric value to an integer
//Syntax
//    INT(<nExp>) --> nInteger
//Arguments
//    <nExp> is a numeric expression to be converted to an integer.
//Returns
//    INT() returns an integer numeric value.
//Description
//    INT() is a numeric function that converts a numeric value to an integer
//    by truncating--not rounding--all digits to the right of the decimal
//    point.  INT() is useful in operations where the decimal portion of a
//    number is not needed.
//Examples
//    -  These examples demonstrate the results of various invocations
//       of the INT() function:
//       ? INT(100.00)               // Result: 100
//       ? INT(.5)                     // Result: 0
//       ? INT(-100.75)               // Result: -100
 return parseInt(exp_);
};
//*******************************************************************************
function INT_testy(){
//*******************************************************************************
 if( INT( 100.00)  ==  100 ) {'OK';} else debugger;
 if( INT(    .5 )  ==    0 ) {'OK';} else debugger;
 if( INT(-100.75)  == -100 ) {'OK';} else debugger;
}
```



```
//*******************************************************************************
function isdate(x) {
//*******************************************************************************
 if( typeof(x)=='date' ) return true;
 return (x != null) && !isNaN(x) && (typeof x.getDate !== "undefined" );
}
```



```
//*******************************************************************************
function ISDIGIT(string_) {
//*******************************************************************************
//Determine if the leftmost character in a character string is a digit
//
//Syntax
//    ISDIGIT(<cString>) --> lBoolean
//Arguments
//    <cString> is the character string to be examined.
//Returns
//    ISDIGIT() returns true (.T.) if the first character of the character
//    string is a digit between zero and nine; otherwise, it returns false
//    (.F.). 
 var z = string_.substr(0,1);
 if( z == '' ) return false;
 return ( '0123456789'.indexOf(z) > -1  );
};
//*******************************************************************************
function ISDIGIT_testy() {
//*******************************************************************************
 if( ISDIGIT("AbcDe")  == false ) {'OK';} else debugger;
 if( ISDIGIT("1abcd")  == true  ) {'OK';} else debugger;
 if( ISDIGIT(".12345") == false ) {'OK';} else debugger;
}
```



```
//*******************************************************************************
function LEFT( string_ , count_ ) {
//*******************************************************************************
//Extract a substring beginning with the first chara
//Syntax
//
//    LEFT(<cString>, <nCount>) -> cSubString
//
 return string_.substr( 0 , count_ );
}
```



```
//*******************************************************************************
function LEN(v){
//*******************************************************************************
//LEN()
//Return the length of a character string or the number of elements in an array
//Syntax
//    LEN(<cString> | <aTarget>) --> nCount
//Arguments
//    <cString> is the character string to count.
//    <aTarget> is the array to count.
//Returns
//    LEN() returns the length of a character string or the number of elements
//    in an array as an integer numeric value.  If the character string is a
//    null string ("") or the array is empty, LEN() returns zero.

 if( VALTYPE(v) == 'C' ) return v.length;
 
 if( VALTYPE(v) == 'A' ){
  if( v.length == 0 ) return 0;
  return v.length-1;
 };
 
 return v.length;
}
```



```
//************************************************************
function LOWER(s){
//************************************************************
 return s.toLowerCase();
}
```



```
//*******************************************************************************
function LTRIM( tekst_ ) {
//*******************************************************************************
 return tekst_.replace(/^\s+/,"");
}
```



```
//************************************************************
function MAX(v1,v2) {
//************************************************************
//MAX()
//Return the larger of two numeric or date values
//Syntax
//    MAX(<nExp1>, <nExp2>) --> nLarger
//    MAX(<dExp1>, <dExp2>) --> dLarger
//Arguments
//    <nExp1> and <nExp2> are the numeric values to be compared.
//    <dExp1> and <dExp2> are the date values to be compared.
//Returns
//    MAX() returns the larger of the two arguments.  The value returned is
//    the same type as the arguments.
//Description
//    MAX() is a numeric and date function that ensures the value of an
//    expression is larger than a specified minimum.  The inverse of MAX() is
//    MIN(), which returns the lesser of two numeric or date values.
//Examples
//    -  In these examples MAX() returns the greater of two numeric
//       values:
//       ? MAX(1, 2)                     // Result: 2
//       ? MAX(2, 1)                     // Result: 2
 return Math.max(v1,v2);
};
//************************************************************
function MAX_testy() {
//************************************************************
 debugger;
 if( MAX( 1, 2) ==  2 ){} else debugger;
 if( MAX( 2, 1) ==  2 ){} else debugger;
 if( MAX(-1,-2) == -1 ){} else debugger;
 if( MAX(-2,-1) == -1 ){} else debugger;
 
}
```



```
//************************************************************
function MIN(v1,v2){
//************************************************************
 return Math.min(v1,v2);
};
//************************************************************
function MIN_testy(){
//************************************************************
 debugger;
 if( MIN( 1, 2) ==  1 ){} else debugger;
 if( MIN( 2, 1) ==  1 ){} else debugger;
 if( MIN(-1,-2) == -2 ){} else debugger;
 if( MIN(-2,-1) == -2 ){} else debugger;
}
```



```
//************************************************************
function MONTH(data_) {
//************************************************************
//Podaje nr miesiąca w zakresie 1..12.
//Uwagi:
//     data_.getMonth() - zwraca wartości od 0..11, więc trzeba dodać 1.
//
 if( typeof(data_)=='date' ) data_ = new Date(data_);//Konwertuje na javascriptowy obiekt Date.
 return ( data_.getMonth() + 1 );
};
//************************************************************
```



```
//----------------------------------------------------------------------
var NIL = null;
//----------------------------------------------------------------------
```



```
//************************************************************
function PADR( exp_ , length_ , fillchar_ ) {
//************************************************************
//PADR(<exp>, <nLength>, [<cFillChar>])
//   -> cPaddedString

 //Domyślnie spacja.
 if( fillchar_ == undefined ) fillchar_ = ' ';
 
 //Jeśli pierwotny tekst jest zbyt długi to zwracam go przyciętego do odpowiedniej długości.
 if( exp_.length > length_ ) return exp_.substr(0,length_);
 
 //Dokładam fillchar_ z prawej strony, aż uzyskam odpowiednią długość.
 while( true ) {
  if( exp_.length == length_ ) return exp_; //Jeśli jest już odpowiednia długość, to zwracam tekst.
  exp_ += fillchar_; //Dokładam fillchar_ z prawej strony.
 };
}
```



```
//************************************************************
function REPLICATE(string_,count_) {
//************************************************************
 var replicate_ = '';
 for (var f = 1; f <= count_; f++ ) {
  replicate_ += string_;
 };
 return replicate_;
}
```



```
//*******************************************************************************
function RIGHT( string_ , count_ ) {
//*******************************************************************************
//RIGHT()
//Return a substring beginning with the rightmost character
//Syntax
//    RIGHT(<cString>, <nCount>) --> cSubString
//Arguments
//    <cString> is the character string from which to extract characters.
//    <nCount> is the number of characters to extract.
//
 //return string_.slice(-count_)//Problem jeśli count_==0 to zwraca cały tekst.Dlatego nie używam slice.
 return string_.substr( string_.length - count_ );
}
```



```
//************************************************************
function ROUND(n,d){
//************************************************************
 //if( d == 2 ) return Math.round(n*100)/100;
 //debugger;//Niezaimplementowane, todo
 return Math.round(n*Math.pow(10,d)) / Math.pow(10,d);
};
//************************************************************
function ROUND_testy(){
//************************************************************
 debugger;
 var n = 12.345453534534;
 if( ROUND(n,-1) == 10              ){}else debugger;
 if( ROUND(n, 0) == 12              ){}else debugger;
 if( ROUND(n, 1) == 12.3            ){}else debugger;
 if( ROUND(n, 2) == 12.35           ){}else debugger;
 if( ROUND(n, 3) == 12.345          ){}else debugger;
 if( ROUND(n, 4) == 12.3455         ){}else debugger;
 if( ROUND(n, 5) == 12.34545        ){}else debugger;
 if( ROUND(n, 6) == 12.345454       ){}else debugger;
 if( ROUND(n, 7) == 12.3454535      ){}else debugger;
 if( ROUND(n, 8) == 12.34545353     ){}else debugger;
 if( ROUND(n, 9) == 12.345453535    ){}else debugger;
 if( ROUND(n,10) == 12.3454535345   ){}else debugger;
 if( ROUND(n,11) == 12.34545353453  ){}else debugger;
 if( ROUND(n,12) == 12.345453534534 ){}else debugger;
 if( ROUND(n,15) == 12.345453534534 ){}else debugger;
}
```



```
//*******************************************************************************
function RTRIM(tekst) {
//*******************************************************************************
//RTRIM()
//Remove trailing spaces from a character string
//Syntax
//    RTRIM(<cString>) --> cTrimString
//Arguments
//    <cString> is the character string to be copied without trailing
//    spaces.
//Returns
//    RTRIM() returns a copy of <cString> with the trailing spaces removed.
//    If <cString> is a null string ("") or all spaces, RTRIM() returns a null
//    string ("").
//Description
//    RTRIM() is a character function that formats character strings.  It is
//    useful when you want to delete trailing spaces while concatenating
//    strings.  This is typically the case with database fields which are
//    stored in fixed-width format.  For example, you can use RTRIM() to
//    concatenate first and last name fields to form a name string.
//    RTRIM() is related to LTRIM() which removes leading spaces, and
//    ALLTRIM() which removes both leading and trailing spaces.  The inverse
//    of ALLTRIM(), LTRIM(), and RTRIM() are the PADC(), PADR(), and PADL()
//    functions which center, right-justify, or left-justify character strings
//    by padding them with fill characters.  RTRIM() is exactly the same as
//    TRIM() in function.
//Notes
//    -  Space characters: The RTRIM() function treats carriage
//       returns, line feeds, and tabs as space characters and removes these
//       as well.
//Examples
//    -  This is a user-defined function in which RTRIM() formats city,
//       state, and zip code fields for labels or form letters:
//       FUNCTION CityState(cCity, cState, cZip)
//          RETURN RTRIM(cCity) + ", " ;
//           + RTRIM(cState) + "  " + cZip
//    -  In this example the user-defined function, CityState(),
//       displays a record from Customer.dbf:
//       USE Customer INDEX CustName NEW
//       SEEK "Kate"
//       ? CityState(City, State, ZipCode)
//       // Result: Athens, GA 10066

 return tekst.replace(/\s+$/,"");
};
//************************************************************
function RTRIM_testy() {
//************************************************************
 debugger;
 if( RTRIM('123'          )=='123'        ) {} else debugger;
 if( RTRIM('123 '         )=='123'        ) {} else debugger;
 if( RTRIM('123  '        )=='123'        ) {} else debugger;
 if( RTRIM(' 123 '        )==' 123'       ) {} else debugger;
 if( RTRIM(' 123  '       )==' 123'       ) {} else debugger;
 if( RTRIM('  123  '      )=='  123'      ) {} else debugger;
 if( RTRIM('123 123'      )=='123 123'    ) {} else debugger;
 if( RTRIM(' 123 123 '    )==' 123 123'   ) {} else debugger;
 if( RTRIM('  123  123  ' )=='  123  123' ) {} else debugger;
}
```



```
//*******************************************************************************
function SECONDS() {
//*******************************************************************************
//Return the number of seconds elapsed since midnight
//TODO: Aktualnie zwraca ilość sekund od północy 1 stycznia 1970.
 return (   (new Date()).getTime() / 1000   );
}
```



```
//-------------------------------------------------------
function SET(n,new_){
//-------------------------------------------------------
//Inspect or change a system setting
//Syntax
//    SET(<nSpecifier>, [<expNewSetting>], [<lOpenMode>])
//       --> CurrentSetting
 var current_ = SET[n];
 if( !( new_ == undefined ) ) SET[n] = new_;
 return current_;
};
//Ustawienia domyślne SET
SET[_SET_DATEFORMAT] = 'DD-MM-YYYY';
```



```
//************************************************************
function SPACE(c) {
//************************************************************
 var s = '';
 for (var f = 1; f <= c; f++ ) s += ' ';
 return s;
}
```



```
//************************************************************
function STR( number_ , length_ , decimals_ ) {
//************************************************************
//STR()
//Convert a numeric expression to a character string
//
//Syntax
//
//    STR(<nNumber>, [<nLength>], [<nDecimals>]) --> cNumber
//
//Arguments
//
//    <nNumber> is the numeric expression to be converted to a character
//    string.
//
//    <nLength> is the length of the character string to return, including
//    decimal digits, decimal point, and sign.
//
//    <nDecimals> is the number of decimal places to return.
//

 if( decimals_==undefined ) decimals_ = 0;//Domyślna wartość po przecinku to zero znaków.

 //Dopasowanie do CLIPPER - korekta znaku minus.
 //W CLIPPER zerowa wartość nie posiada znaku minus.
 //CLIPPER:    STR( -0.000001   ,  5 , 2 ) -> ' 0.00'
 //Javascript: (-0.000001).toFixed(2)      -> '-0.00'
 //
 //CLIPPER:    STR( -0.000001   ,  5 , 0 ) -> '    0'
 //Javascript: (-0.000001).toFixed(0)      -> '-0'
 //
 if( number_ < 0 ) {
  var n = Math.round(number_*Math.pow(10,decimals_));
  if( n == 0 ) number_ = Math.abs(number_);
 };
 
 var s = number_.toFixed(decimals_);
 
 if( length_ == undefined ) return s;
 
 if( s.length > length_ ) return REPLICATE('*',length_); //String nie mieści się w założonej długości.
 while( s.length < length_ ) s = ' ' + s; //Dokładanie spacji od lewej strony, aby była odpowiednia długość tekstu.
 
 return s;
};
//************************************************************
function STR_testy() {
//************************************************************
 debugger;
 if( STR(      1      ,  1     ) != '1'            ) debugger;
 if( STR(     -1      ,  1     ) != '*'            ) debugger;
 if( STR(     -1      ,  2     ) != '-1'           ) debugger;
 if( STR(  12345.6789 , 10     ) != '     12346'   ) debugger;
 if( STR( -12345.6789 , 10     ) != '    -12346'   ) debugger;
 if( STR(  12345.6789 , 10 , 1 ) != '   12345.7'   ) debugger;
 if( STR( -12345.6789 , 10 , 1 ) != '  -12345.7'   ) debugger;
 if( STR(  12345.6789 , 12 , 6 ) != '12345.678900' ) debugger;
 if( STR( -12345.6789 , 12 , 6 ) != '************' ) debugger;
 if( STR(  0.000001   ,  5 , 2 ) != ' 0.00'        ) debugger;
 if( STR( -0.000001   ,  5 , 2 ) != ' 0.00'        ) debugger;
 if( STR( -0.000001   ,  5 , 0 ) != '    0'        ) debugger;
}
```



```
//************************************************************
function STRTRAN( string_ , search_ , replace_ ) {
//************************************************************
 var split_ = string_.split(search_);
 var join_  = split_.join(replace_);
 return join_;
};
//************************************************************
```



```
//************************************************************
function STRZERO(liczba_,len_) {
//************************************************************
//
 var strzero = liczba_.toString();
// 
// strzero = String(len_-len(strzero),"0") & strzero
//  STRZERO_ := REPLICATE('0',LEN_-LEN(STRZERO_)) + STRZERO_
 return REPLICATE('0',len_-strzero.length ) + strzero ;
};
//************************************************************
```



```
//************************************************************
function SUBSTR( s_ , start_ , len_ ) {
//************************************************************
 if( s_ === null ) s_ = '';
 start_--;
 return s_.substr(start_,len_);
}
```



```
//************************************************************
function TIME() {
//************************************************************
//Zwraca aktualny czas w formacie tekstowym 'GG:MM:SS'
 var d = new Date;
 var s = '';
 if( d.getHours()   <  10 ) s += '0';
                            s += d.getHours();
                            s += ':';
 if( d.getMinutes() <  10 ) s += '0';
                            s += d.getMinutes();
                            s += ':';
 if( d.getSeconds() <  10 ) s += '0';
                            s += d.getSeconds();
 return s;
};
//************************************************************
```



```
//************************************************************
function TRAN( v , f ) {
//************************************************************
//

 if( typeof v == 'number' ) {
  
  //debugger;
  
  if( f == '999 999 999.99' ) {
   var s = v.toFixed(2);
   if( s.length > 12 ) return s;
   while( s.length < 12 ) s = ' ' + s; //'   345678.12'
   s = s.substr(0,3) + ' ' + s.substr(3,3) + ' ' + s.substr(6);
   return s;
  };
  
 };
 

 debugger;//Niezaimplementowany szablon
 
 return v;
};
//************************************************************
```



```
//************************************************************
function UPPER(s) {
//************************************************************
//UPPER()
//Convert lowercase characters to uppercase
//Syntax
//    UPPER(<cString>) --> cUpperString
//Arguments
//    <cString> is the character string to be converted.
//Returns
//    UPPER() returns a copy of <cString> with all alphabetical characters
//    converted to uppercase.  All other characters remain the same as in the
//    original string.
//Description
//    UPPER() is a character function that converts lowercase and mixed case
//    strings to uppercase.  It is related to LOWER() which converts uppercase
//    and mixed case strings to lowercase.  UPPER() is related to the
//    ISUPPER() and ISLOWER() functions which determine whether a string
//    begins with an uppercase or lowercase letter.
//    UPPER() is generally used to format character strings for display
//    purposes.  It can, however, be used to normalize strings for case-
//    independent comparison or INDEXing purposes.
//Examples
//    -  These examples illustrate the effects of UPPER():
//       ? UPPER("a string")           // Result: A STRING
//       ? UPPER("123 char = <>")      // Result: 123 CHAR = <>
//
 return s.toUpperCase();
};
//************************************************************
function UPPER_testy() {
//************************************************************
 debugger;
 if( UPPER("a string"     )=="A STRING"      ) {} else debugger;
 if( UPPER("123 char = <>")=="123 CHAR = <>" ) {} else debugger;

}
```



```
//************************************************************
function VAL(tekst_) {
//************************************************************
//Przekształca tekst na liczbę.
 var val_ = parseFloat( tekst_ );
 if( isNaN(val_) ) val_ = 0;
 return val_;
};
//************************************************************
```



```
//************************************************************
function VALTYPE(v) {
//************************************************************
//VALTYPE()
// Determine the data type returned by an expression
// Syntax
//
//     VALTYPE(<exp>) --> cType
//
// Arguments
//
//     <exp> is an expression of any type.
//
// Returns
//
//     VALTYPE() returns a single character representing the data type returned
//     by <exp>.  VALTYPE() returns one of the following characters:
//
//     VALTYPE() Return Values  Javascript
//     Returns   Meaning        
//     A         Array          v instanceof Array
//     B         Block          typeof(v)=="function"
//     C         Character      typeof(v)=="string"
//     D         Date           typeof(v)=="date" || v instanceof Date
//     L         Logical        typeof(v)=="boolean"
//     M         Memo           brak implementacji: "X"
//     N         Numeric        typeof(v)=="number"
//     O         Object         "object"
//     U         NIL            "undefined"
//                              inne typy: X

 if( v instanceof Array                     ) return "A";
 if( typeof(v)=="function"                  ) return "B";
 if( typeof(v)=="string"                    ) return "C";
 if( typeof(v)=="date" || v instanceof Date ) return "D";
 if( typeof(v)=="boolean"                   ) return "L";
 if( typeof(v)=="number"                    ) return "N";
 if( typeof(v)=="object"                    ) return "O";
 if( typeof(v)=="undefined"                 ) return "U";

 return "X";
};
//************************************************************
```



```
//************************************************************
function YEAR(d) {
//************************************************************
//Convert a date value to the year as a numeric value
//Syntax
//    YEAR(<dDate>) --> nYear
//Arguments
//    <dDate> is the date value to be converted.
//Returns
//    YEAR() returns the year of the specified date value including the
//    century digits as a four-digit numeric value.  The value returned is not
//    affected by the current DATE or CENTURY format.  Specifying a null date
//    (CTOD("")) returns zero.
//
 if( EMPTY(d) ) return 0;
 if( typeof(d)=='date' ) d = new Date(d);//Konwertuje na javascriptowy obiekt Date.
 return ( d.getFullYear() );
};
//************************************************************
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


