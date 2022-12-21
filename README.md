# mariuszmaciaszek.github.io



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


