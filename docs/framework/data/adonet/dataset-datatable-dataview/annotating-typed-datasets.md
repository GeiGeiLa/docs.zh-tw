---
title: 註釋具類型資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: c66a11e0662cd007797243c136ec0617ce5be47c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513143"
---
# <a name="annotating-typed-datasets"></a>註釋具類型資料集
註釋可讓您在無需修改基礎結構描述的情況下，修改具型別之 <xref:System.Data.DataSet> 中的項目名稱。 修改基礎結構描述中元素的名稱可能會造成具型別的**資料集**來執行不存在於資料來源，以及遺失的資料來源中存在的物件參考的物件參考。  
  
 使用註釋，您可以自訂物件的名稱將具型別的**資料集**使用更有意義的名稱，使程式碼更容易閱讀，將具型別的**DataSet**用戶端使用，同時讓您更輕鬆基礎結構描述保持不變。 例如，下列結構描述項目**客戶**的資料表**Northwind**資料庫會導致**DataRow**物件名稱**Datarow**並<xref:System.Data.DataRowCollection>名為**客戶**。  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 A **DataRowCollection**名稱**客戶**才有意義的用戶端程式碼，但**DataRow**名稱**Datarow**也會產生誤導因為它是單一物件。 此外，在一般情況下，物件會參考而不需要**資料列**識別碼，而是會直接稱為**客戶**物件。 解決方法是結構描述註解並找出新的名稱，如**DataRow**並**DataRowCollection**物件。 下列為上述結構描述的標註版本。  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 指定**typedName**的值**客戶**將會導致**DataRow**物件名稱**客戶**。 指定**typedPlural**的值**客戶**保留**DataRowCollection**名稱**客戶**。  
  
 下列表格顯示可供使用的註釋。  
  
|註釋|描述|  
|----------------|-----------------|  
|**typedName**|物件名稱。|  
|**typedPlural**|物件集合名稱。|  
|**typedParent**|在父關聯性中所參考的物件名稱。|  
|**typedChildren**|從子關聯性傳回物件的方法名稱。|  
|**nullValue**|如果基礎值是值**DBNull**。 請參閱下列表格**nullValue**註解。 預設值是 **_throw**。|  
  
 下表顯示可針對指定的值**nullValue**註釋。  
  
|nullValue 值|描述|  
|---------------------|-----------------|  
|*取代值*|指定要傳回的值。 傳回值必須與項目的型別相符。 例如，使用 `nullValue="0"` 可為 null 整數欄位傳回 0。|  
|**_throw**|擲回例外狀況。 這是預設值。|  
|**_null**|如果遇到基本型別，則會傳回 Null 參考或發生例外狀況。|  
|**_empty**|針對字串，傳回**String.Empty**，否則會傳回空的建構函式建立的物件。 如果遇到基本型別，則會發生例外狀況。|  
  
 下表顯示之物件的預設值，在具型別**資料集**和可用的註解。  
  
|物件/方法/事件|預設|註釋|  
|---------------------------|-------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**DataTable**方法|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**Property**|PropertyName|typedName|  
|**子**存取子|GetChildTableNameRows|typedChildren|  
|**父**存取子|TableNameRow|typedParent|  
|**資料集**事件|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 若使用具型別**資料集**註解，您必須包含下列**xmlns** XML 結構描述定義語言 (XSD) 結構描述中的參考。 (若要從資料庫資料表建立 xsd，請參閱<xref:System.Data.DataSet.WriteXmlSchema%2A>或是[使用 Visual Studio 中的資料集](https://msdn.microsoft.com/library/8bw9ksd6.aspx))。  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 以下是範例的註解式結構描述會公開**客戶**的資料表**Northwind**資料庫的關聯**訂單**包含的資料表。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"   
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 下列程式碼範例會使用強型別**資料集**從範例結構描述建立。 它會使用其中一個<xref:System.Data.SqlClient.SqlDataAdapter>來填入**客戶**資料表，另一個<xref:System.Data.SqlClient.SqlDataAdapter>填入**訂單**資料表。 強型別**資料集**定義**Datarelation**。  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",   
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new   
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =   
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [具類型的 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
