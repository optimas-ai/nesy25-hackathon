# Ontology Documentation

## Classes

### Supplier_xnt

**description**: The supplier

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Supplier_xnt

**Properties**:
- supplier_id_xnt: STRING (description - The supplier id)
- supplier_name_xnt: STRING (description - The supplier name)
- reliability_score_xnt: NUMBER_CARDINAL (description - The reliability score)

**Direct Relationships**:
- Supplies_xnt to Inventory_Item_xnt (min: 1, max: 32767)

**Inherited Relationships**:
- None


### Location_xnt

**description**: The location

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Location_xnt

**Properties**:
- location_id_xnt: STRING (description - The location id)
- location_name_xnt: STRING (description - The location name)
- coordinates_xnt: STRING (description - The coordinates)
- capacity_limit_xnt: NUMBER_CARDINAL (description - The capacity limit)

**Direct Relationships**:
- None

**Inherited Relationships**:
- None


### Customer_xnt

**description**: The customer

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Customer_xnt

**Properties**:
- customer_id_xnt: STRING (description - The customer id)
- customer_priority_xnt: STRING (description - The customer priority)
- contact_email_xnt: STRING (description - The contact email)

**Direct Relationships**:
- Triggers_Order_xnt to Order_xnt (min: 1, max: 32767)

**Inherited Relationships**:
- None


### Warehouse_xnt

**description**: The warehouse

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Location_xnt → Warehouse_xnt

**Properties**:
- storage_type_xnt: STRING (description - The storage type)
- operational_hours_xnt: STRING (description - The operational hours)

**Direct Relationships**:
- None

**Inherited Relationships**:
- None


### Delivery_Schedule_xnt

**description**: The delivery schedule

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Delivery_Schedule_xnt

**Properties**:
- schedule_id_xnt: STRING (description - The schedule id)
- deliver_date_xnt: TIME_ABSOLUTE_MILLIS (description - The deliver date)
- priority_level_xnt: STRING (description - The priority level)
- backup_delivery_date_xnt: TIME_ABSOLUTE_MILLIS (description - The backup delivery date)

**Direct Relationships**:
- None

**Inherited Relationships**:
- None


### Port_xnt

**description**: The port

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Location_xnt → Port_xnt

**Properties**:
- port_type_xnt: STRING (description - The port type)
- customs_clearance_time_xnt: NUMBER_CARDINAL (description - The customs clearance time)

**Direct Relationships**:
- None

**Inherited Relationships**:
- None


### Truck_xnt

**description**: The truck

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Vehicle_xnt → Truck_xnt

**Properties**:
- max_load_weight_xnt: NUMBER_CARDINAL (description - The max load weight)
- driver_assigned_xnt: STRING (description - The driver assigned)

**Direct Relationships**:
- None

**Inherited Relationships**:
- Operates_On_xnt to Route_xnt (from Vehicle_xnt)


### Vehicle_xnt

**description**: The vehicle

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Vehicle_xnt

**Properties**:
- vehicle_id_xnt: STRING (description - The vehicle id)
- vehicle_capacity_xnt: NUMBER_CARDINAL (description - The vehicle capacity)
- fuel_type_xnt: STRING (description - The fuel type)
- maintenance_due_xnt: TIME_ABSOLUTE_MILLIS (description - The maintenance due)

**Direct Relationships**:
- Operates_On_xnt to Route_xnt (min: 0, max: 32767)

**Inherited Relationships**:
- None


### Inventory_Item_xnt

**description**: The inventory item

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Inventory_Item_xnt

**Properties**:
- item_id_xnt: STRING (description - The item id)
- inventory_level_xnt: NUMBER_CARDINAL (description - The inventory level)
- unit_price_xnt: NUMBER_CARDINAL (description - The unit price)
- product_category_xnt: STRING (description - The product category)

**Direct Relationships**:
- None

**Inherited Relationships**:
- None


### Order_xnt

**description**: The order

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Order_xnt

**Properties**:
- order_id_xnt: STRING (description - The order id)
- order_date_xnt: TIME_ABSOLUTE_MILLIS (description - The order date)
- order_quantity_xnt: NUMBER_CARDINAL (description - The order quantity)
- order_status_xnt: STRING (description - The order status)

**Direct Relationships**:
- Generates_xnt to Shipment_xnt (min: 1, max: 1)

**Inherited Relationships**:
- None


### Shipment_xnt

**description**: The shipment

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Shipment_xnt

**Properties**:
- shipment_id_xnt: STRING (description - The shipment id)
- delivery_date_xnt: TIME_ABSOLUTE_MILLIS (description - The delivery date)
- shipment_status_xnt: STRING (description - The shipment status)
- transport_cost_xnt: NUMBER_CARDINAL (description - The transport cost)

**Direct Relationships**:
- Transported_By_xnt to Vehicle_xnt (min: 1, max: 1)
- Follows_Route_xnt to Route_xnt (min: 0, max: 1)
- Contains_xnt to Package_xnt (min: 1, max: 32767)

**Inherited Relationships**:
- None


### Ship_xnt

**description**: The ship

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Vehicle_xnt → Ship_xnt

**Properties**:
- container_capacity_xnt: NUMBER_CARDINAL (description - The container capacity)
- port_of_registry_xnt: STRING (description - The port of registry)

**Direct Relationships**:
- None

**Inherited Relationships**:
- Operates_On_xnt to Route_xnt (from Vehicle_xnt)


### Disruption_Event_xnt

**description**: The disruption event

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Disruption_Event_xnt

**Properties**:
- event_id_xnt: STRING (description - The event id)
- delay_duration_xnt: NUMBER_CARDINAL (description - The delay duration)
- event_type_xnt: STRING (description - The event type)
- event_start_time_xnt: TIME_ABSOLUTE_MILLIS (description - The event start time)

**Direct Relationships**:
- Causes_Delay_xnt to Shipment_xnt (min: 0, max: 32767)
- Affects_Schedule_xnt to Delivery_Schedule_xnt (min: 0, max: 32767)

**Inherited Relationships**:
- None


### Package_xnt

**description**: The package

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Package_xnt

**Properties**:
- package_id_xnt: STRING (description - The package id)
- package_weight_xnt: NUMBER_CARDINAL (description - The package weight)
- package_type_xnt: STRING (description - The package type)
- fragility_level_xnt: STRING (description - The fragility level)

**Direct Relationships**:
- Stored_At_xnt to Warehouse_xnt (min: 0, max: 1)
- Consists_Of_xnt to Inventory_Item_xnt (min: 0, max: 32767)

**Inherited Relationships**:
- None


### Route_xnt

**description**: The route

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Route_xnt

**Properties**:
- route_id_xnt: STRING (description - The route id)
- route_distance_xnt: NUMBER_CARDINAL (description - The route distance)
- estimated_transit_time_xnt: NUMBER_CARDINAL (description - The estimated transit time)
- route_type_xnt: STRING (description - The route type)

**Direct Relationships**:
- Has_Origin_xnt to Location_xnt (min: 1, max: 1)
- Has_Destination_xnt to Location_xnt (min: 1, max: 1)

**Inherited Relationships**:
- None


## Relationships

### Follows_Route_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Has_Destination_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Transported_By_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Triggers_Order_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Has_Origin_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Contains_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Causes_Delay_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Consists_Of_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Supplies_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Operates_On_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Stored_At_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Generates_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


### Affects_Schedule_xnt

**Extends**: AbstractOntologyRelationship

**Properties**:
- None


