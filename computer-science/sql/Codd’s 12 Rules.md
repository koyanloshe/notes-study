# Codd’s 12 Rules

## 1. Information rule

Data stored in  database may it be user data or metadata must be a value of some table cell.

## 2. Guaranteed access rule

Every value is guaranteed to be accessible logically with a combination of table-name, primary-key, attribute-name. No other means such as pointers can be used to access data. 

## 3. Systematic treatment of null values

Null values in DB must be given a systematic and uniform treatment.

## 4. Active Online Catalog

Structure description of the entire database must be stored in an online catalog known as a **data dictionary **which can be accessed by authorised users.

## 5. Comprehensive Data Sub-language Rule

Language must have linear syntax that supports data-definition, data manipulation, transaction management.
 
## 6. View Updating Rule

All the views of a database which can theoretically be updated must also be updatable by the system.

## 7. High level insert, update, and delete rule

Must not be limited to a single row. It must also support union intersection and minus operations to yield sets to data records.

## 8. Physical Data Independence

Data stored in a DB must be independent of the apps that access the database Any change in the physical structure of a DB must not have any impact on how the data is being accessed by external apps.

## 9. Logical Data Independence

Logical data in a DB must be independent of its user’s view/app. Any change in logical data must not affect the apps using it.

## 10. Integrity independence

A DB must be independent of the app that uses it. All its integrity constraints can be independently modified without the need of any change in the app. The rule makes a DB independent of the front end.

## 11. Distribution independence 

End user must not be able to see that the data is distributed over various locations. Users should always get the impression that the data is located at one site only. This rule has been regarded as the foundation of distributed database systems.

## 12. Non Subversion rule

If a system has an interface that provides access to low level records then the interface must not be able to subvert the system and bypass security and integrity constraints.

