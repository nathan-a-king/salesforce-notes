# Variables and Heap

- Heap size limit for an Apex program is 6 MB.
- Primitive data types
  - Boolean
  - String
  - Integer
  - Long
  - Decimal
  - Double
  - Date
  - Time
  - Datetime
  - Blob
  - ID
    - 15-digit is case sensitive
    - 18-digit is **not** case sensitive

  public class QuickActionHandler {

    // Define the method that will be executed when the Quick Action is clicked
    public static void executeQuickAction(List<sObject> records) {
        List<String> floodZones = new List<String>();
        List<String> parcelDescriptions = new List<String>();

        // Loop through the records passed in and retrieve data from the specified fields
        for (sObject record : records) {
            if (record.getSObjectType() == YourObject__c.SObjectType) {
                YourObject__c obj = (YourObject__c)record;
                if (obj.Flood_Zone__c != null) {
                    floodZones.add(obj.Flood_Zone__c);
                }
                if (obj.Parcel_Description__c != null) {
                    parcelDescriptions.add(obj.Parcel_Description__c);
                }
            }
        }

        // You can now use the data from floodZones and parcelDescriptions as needed
        // For example, you can log the data or perform any other operations
        // Make sure to replace YourObject__c with the actual API name of your object.
    }
}

In this code:

Replace YourObject__c with the API name of the object where you want to retrieve data from the fields "Flood_Zone__c" and "Parcel_Description__c."

This class defines a method executeQuickAction that takes a list of sObjects as a parameter. When the Quick Action is clicked, Salesforce will pass the selected records to this method.

Inside the method, it loops through the records and checks if they are instances of the specified object type. It then retrieves the values from the "Flood_Zone__c" and "Parcel_Description__c" fields for each record and stores them in separate lists.

You can customize the code to perform specific operations with the retrieved data, such as logging it or any other business logic you require.

Make sure to create a Quick Action in Salesforce and associate it with this Apex class to trigger the executeQuickAction method when the Quick Action is clicked on the desired object's detail page.
