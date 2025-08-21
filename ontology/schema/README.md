# Ontology Documentation

## Classes

### Supplier_xnt

**description**: Entity providing goods.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Supplier_xnt

**Properties**:
- supplier_id_xnt: STRING (description - Unique identifier for the supplier.)
- supplier_name_xnt: STRING (description - Name of the supplier.)
- reliability_score_xnt: NUMBER_CARDINAL (description - Reliability rating of the supplier. Example 4.8)

**Direct Relationships**:
- Supplies_xnt to Inventory_Item_xnt (min: 1, max: 32767)

**Inherited Relationships**:
- None


### Location_xnt

**description**: A geographic point. Example city or warehouse address.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Location_xnt

**Properties**:
- location_id_xnt: STRING (description - Unique identifier for the location.)
- location_name_xnt: STRING (description - Name of the geographic location or facility.)
- coordinates_xnt: STRING (description - Geographic coordinates of the location. Latitude and longitude.)
- capacity_limit_xnt: NUMBER_CARDINAL (description - Maximum storage or processing capacity of location.)

**Direct Relationships**:
- None

**Inherited Relationships**:
- None


### Customer_xnt

**description**: Entity receiving goods.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Customer_xnt

**Properties**:
- customer_id_xnt: STRING (description - Unique identifier for the customer.)
- customer_priority_xnt: STRING (description - Priority level of the customer. Example  High Medium.)
- contact_email_xnt: STRING (description - Customers contact email address.)

**Direct Relationships**:
- Triggers_Order_xnt to Order_xnt (min: 1, max: 32767)

**Inherited Relationships**:
- None


### Warehouse_xnt

**description**: Storage facility for goods. Subclass of Location.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Location_xnt → Warehouse_xnt

**Properties**:
- storage_type_xnt: STRING (description - Type of storage. Example  Dry or Refrigerated.)
- operational_hours_xnt: STRING (description - Operating hours of the warehouse.)

**Direct Relationships**:
- None

**Inherited Relationships**:
- None


### Delivery_Schedule_xnt

**description**: Planned timeline for shipment delivery.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Delivery_Schedule_xnt

**Properties**:
- schedule_id_xnt: STRING (description - Unique identifier for the delivery schedule.)
- deliver_date_xnt: TIME_ABSOLUTE_MILLIS (description - Scheduled date and time for delivery.)
- priority_level_xnt: STRING (description - Priority of the delivery schedule. Example Urgent.)
- backup_delivery_date_xnt: TIME_ABSOLUTE_MILLIS (description - Fallback delivery date for contingency planning.)

**Direct Relationships**:
- None

**Inherited Relationships**:
- None


### Port_xnt

**description**: A hub for loading and unloading shipments. Example seaport or airport.  Subclass of Location.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Location_xnt → Port_xnt

**Properties**:
- port_type_xnt: STRING (description - Type of port. Example Seaport Airport.)
- customs_clearance_time_xnt: NUMBER_CARDINAL (description - Average customs clearance time in hours.)

**Direct Relationships**:
- None

**Inherited Relationships**:
- None


### Truck_xnt

**description**: Specific land transport. Subclass of Vehicle.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Vehicle_xnt → Truck_xnt

**Properties**:
- max_load_weight_xnt: NUMBER_CARDINAL (description - Maximum load weight in tons for the truck.)
- driver_assigned_xnt: STRING (description - Driver assigned to operate the truck.)

**Direct Relationships**:
- None

**Inherited Relationships**:
- Operates_On_xnt to Route_xnt (from Vehicle_xnt)


### Vehicle_xnt

**description**: A mode of transport. Example truck or ship.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Vehicle_xnt

**Properties**:
- vehicle_id_xnt: STRING (description - Unique identifier for the vehicle.)
- vehicle_capacity_xnt: NUMBER_CARDINAL (description - Maximum number of packages the vehicle carries.)
- fuel_type_xnt: STRING (description - Fuel type used by the vehicle. Example Diesel.)
- maintenance_due_xnt: TIME_ABSOLUTE_MILLIS (description - Next scheduled maintenance date for the vehicle.)

**Direct Relationships**:
- Operates_On_xnt to Route_xnt (min: 0, max: 32767)

**Inherited Relationships**:
- None


### Inventory_Item_xnt

**description**: Specific stock in a warehouse or store.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Inventory_Item_xnt

**Properties**:
- item_id_xnt: STRING (description - Unique identifier for the inventory item.)
- inventory_level_xnt: NUMBER_CARDINAL (description - Current stock quantity of the item.)
- unit_price_xnt: NUMBER_CARDINAL (description - Price per unit in USD.)
- product_category_xnt: STRING (description - Category of the item. Example)

**Direct Relationships**:
- None

**Inherited Relationships**:
- None


### Order_xnt

**description**: A request for goods from supplier to customer.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Order_xnt

**Properties**:
- order_id_xnt: STRING (description - Unique identifier for the order.)
- order_date_xnt: TIME_ABSOLUTE_MILLIS (description - Date and time the order was placed.)
- order_quantity_xnt: NUMBER_CARDINAL (description - Number of items ordered.)
- order_status_xnt: STRING (description - Current status of the order. Example Pending.)

**Direct Relationships**:
- Generates_xnt to Shipment_xnt (min: 1, max: 1)

**Inherited Relationships**:
- None


### Shipment_xnt

**description**: A package or cargo being transported.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Shipment_xnt

**Properties**:
- shipment_id_xnt: STRING (description - Unique identifier for the shipment.)
- delivery_date_xnt: TIME_ABSOLUTE_MILLIS (description - Scheduled delivery time of the shipment.)
- shipment_status_xnt: STRING (description - Current state of the shipment. Example In Transit.)
- transport_cost_xnt: NUMBER_CARDINAL (description - Cost of transporting the shipment in USD.)

**Direct Relationships**:
- Transported_By_xnt to Vehicle_xnt (min: 1, max: 1)
- Follows_Route_xnt to Route_xnt (min: 0, max: 1)
- Contains_xnt to Package_xnt (min: 1, max: 32767)

**Inherited Relationships**:
- None


### Ship_xnt

**description**: Specific sea transport. Subclass of Vehicle.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Vehicle_xnt → Ship_xnt

**Properties**:
- container_capacity_xnt: NUMBER_CARDINAL (description - Maximum number of containers the ship carries.)
- port_of_registry_xnt: STRING (description - Home port where the ship is registered.)

**Direct Relationships**:
- None

**Inherited Relationships**:
- Operates_On_xnt to Route_xnt (from Vehicle_xnt)


### Disruption_Event_xnt

**description**: An event causing delays or issues. Example  weather or strike.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Disruption_Event_xnt

**Properties**:
- event_id_xnt: STRING (description - Unique identifier for the disruption event.)
- delay_duration_xnt: NUMBER_CARDINAL (description - Duration of delay caused by event in hours.)
- event_type_xnt: STRING (description - Type of disruption. Example Storm Strike.)
- event_start_time_xnt: TIME_ABSOLUTE_MILLIS (description - Start time of the disruption event.)

**Direct Relationships**:
- Causes_Delay_xnt to Shipment_xnt (min: 0, max: 32767)
- Affects_Schedule_xnt to Delivery_Schedule_xnt (min: 0, max: 32767)

**Inherited Relationships**:
- None


### Package_xnt

**description**: Individual items within a shipment. Example boxes or pallets.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Package_xnt

**Properties**:
- package_id_xnt: STRING (description - Unique identifier for the package.)
- package_weight_xnt: NUMBER_CARDINAL (description - Weight of the package in kilograms.)
- package_type_xnt: STRING (description - Type of package. Example Box, Pallet.)
- fragility_level_xnt: STRING (description - Fragility rating of the package. Example High.)

**Direct Relationships**:
- Stored_At_xnt to Warehouse_xnt (min: 0, max: 1)
- Consists_Of_xnt to Inventory_Item_xnt (min: 0, max: 32767)

**Inherited Relationships**:
- None


### Route_xnt

**description**: The path a shipment takes between locations.

**annotation**: null

**Inheritance Path**: AbstractOntologyClass → Route_xnt

**Properties**:
- route_id_xnt: STRING (description - Unique identifier for the route.)
- route_distance_xnt: NUMBER_CARDINAL (description - Distance of the route in kilometers.)
- estimated_transit_time_xnt: NUMBER_CARDINAL (description - Estimated transit time of the route in hours.)
- route_type_xnt: STRING (description - Transport mode of the route. Land or Sea.)

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


