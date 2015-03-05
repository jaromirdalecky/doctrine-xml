# Doctrine XML

An XML representation for Doctrine database schemas.

## Online normalization and validation tool

http://concrete5.github.io/doctrine-xml/


## Complete example

```xml
<?xml version="1.0" encoding="UTF-8"?>
<schema xmlns="http://www.concrete5.org/doctrine-xml/0.5"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://www.concrete5.org/doctrine-xml/0.5 http://concrete5.github.io/doctrine-xml/doctrine-xml-0.5.xsd"
>

  <table name="Companies" engine="INNODB" comment="List of companies">
    <field name="Id" type="integer" comment="Record identifier">
      <unsigned />
      <autoincrement />
      <key />
    </field>
    <field name="Name" type="string" size="50" comment="Company name">
      <notnull />
    </field>
  </table>

  <table name="Employees" engine="INNODB">
    <field name="Id" type="integer">
      <unsigned />
      <autoincrement />
      <key />
    </field>
    <field name="IdentificationCode" type="string" size="20" />
    <field name="Company" type="integer">
      <unsigned />
      <notnull />
    </field>
    <field name="FirstName" type="string" size="50" />
    <field name="LastName" type="string" size="50">
      <notnull />
    </field>
    <field name="Income" type="decimal" size="10.2">
      <default value="1000" />
    </field>
    <field name="HiredOn" type="datetime">
      <deftimestamp />
    </field>
    <index>
      <fulltext />
      <col>FirstName</col>
    </index>
    <index>
      <unique />
      <col>IdentificationCode</col>
    </index>
    <references table="Companies" onupdate="cascade" ondelete="restrict">
      <column local="Company" foreign="Id" />
    </references>
  </table>

</schema>
```