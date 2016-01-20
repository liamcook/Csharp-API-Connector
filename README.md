C# Majestic API Connector
=========================

The C# connector is written using Visual Studio 2015 and targets .NET Framework 3.5.

```C#
var api = new APIService("MY_API_KEY", "http://api.majestic.com/api_command");

var parameters = new Dictionary<string, string>()
{
	{"items", "1"},
	{"item0", "majestic.com"}
};

Response response = api.ExecuteCommand("GetIndexItemInfo", parameters);

if (response.IsOK())
{
	DataTable dataTable = response.GetTableForName("Results");
	List<Dictionary<string, string>> rows = dataTable.GetTableRows();
	Dictionary<string, string> result = rows[0];

	Console.WriteLine(result["ExtBackLinks"]);
}
else
{
	Console.WriteLine(response.GetErrorMessage());
}
```

A full list of available commands can be found within the [developer documentation](http://dev.majestic.com/api/commands/).