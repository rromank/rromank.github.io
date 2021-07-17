## Hibernate inheritance models

#### Mapped Superclasses

* A mapped superclass provides persistent entity state and mapping information but is not itself an entity.
* A mapped superclass, unlike an entity, does not allow querying, persisting, or relationships to the superclass.
* @MappedSuperclass annotation is used to designate a class as mapped superclass.
* All mappings annotation can be used on the root class except for @Entity. Also persistent relationships defined by a mapped superclass must be unidirectional.
* Mapping information may be overridden in the subclasses by using the @AttributeOverride and @AssociationOverride annotations.
* Both abstract and concrete classes may be specified as mapped superclasses.
* It is similar to table per class inheritance but no table joins or inheritance exists in data model. There's no table for the mapped superclass. Inheritance only exists in object model.
* The main disadvantage of using mapped superclass is that we cannot load all entities (subclasses) represented by the mapped superclass, i.e., polymorphic queries are not possible.

![mapped_superclass](https://www.logicbig.com/tutorials/java-ee-tutorial/jpa/mapped-super-class/images/overview.png)


#### Table per Class

* In this strategy, the superclass and subclasses in a hierarchy are mapped to different individual tables.
* All super/subclasses tables store all fields of that class plus the ones which are inherited from the super class.
* The annotation @Inheritance is used on the root entity class with strategy = InheritanceType.TABLE_PER_CLASS.
* @DiscriminatorColumn and @DiscriminatorValue are not required to be used in this strategy.
* @Entity and other meta-data annotations are used on the root and subclasses as usual.
* @Id field should only be defined in the root class.
* The root class can be abstract or a concrete class.
* For JPA implementations, support for the table per concrete class inheritance mapping strategy is optional. That means applications that use this mapping strategy might not be portable.
* This strategy has the disadvantage of repeating same attributes in the tables. This strategy also uses SQL UNION queries (or a separate SQL query per subclass). When the concrete subclass is not known, the related object could be in any of the subclass tables, making joins through the relation impossible, hence providing poor support for polymorphic relationships.

![table_pre_class](https://www.logicbig.com/tutorials/java-ee-tutorial/jpa/table-per-class-inheritance/images/overview.png)


#### Single Table

* In this strategy, all the classes in a hierarchy are mapped to a single table.
* The annotation @Inheritance is used on the root entity class with strategy = InheritanceType.SINGLE_TABLE.
* @DiscriminatorColumn is used on the root entity class to specify the discriminator column attributes. Discriminator is a way to differentiate rows belonging to different classes in the hierarchy.
* @DiscriminatorValue is used on each persistable concrete class to specify a unique discriminator value.
* @Entity and other meta-data annotations are used on the root and subclasses as usual.
* @Id field should only be defined in the root class.
* The root class can be abstract or a concrete class. An abstract entity differs from a concrete entity only in that it cannot be directly instantiated.
* This is the default inheritance strategy. That means if we don't specify the strategy attribute of @Inheritance annotation on the the root class or don't use this annotation at all , then InheritanceType.SINGLE_TABLE strategy is assumed.
* This strategy has the disadvantage of having rows with null column values for which the entity has no corresponding fields.

![single_table](https://www.logicbig.com/tutorials/java-ee-tutorial/jpa/single-table-inheritance/images/overview.png)


#### Joined Subclass

* In this strategy, the superclass and subclasses in a hierarchy are mapped to different individual tables.
* The tables corresponding to subclasses do not contain the field from the superclass, except for the @Id fields which are mapped to the primary key(s) of each table.
* The primary key column(s) of the subclass table serves as a foreign key to the primary key of the superclass table.
* The annotation @Inheritance is used on the root entity class with strategy = InheritanceType.JOINED.
* @DiscriminatorColumn is used on the root entity class to specify the discriminator column attributes. Discriminator is a way to differentiate rows belonging to different subclasses in the root table.
* @DiscriminatorValue is used on each persistable subclass to specify a unique discriminator value.
* @Entity and other meta-data annotations are used on the root and subclasses as usual.
* @Id field should only be defined in the root class.
* The root class can be abstract or a concrete class.
* This strategy has the disadvantage of using one or more join queries to instantiate instances of a subclass. In deep class hierarchies, this may lead to unacceptable performance hit.

![joined_subclass](https://www.logicbig.com/tutorials/java-ee-tutorial/jpa/joined-table-inheritance/images/overview.png)

