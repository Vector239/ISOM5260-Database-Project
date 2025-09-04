-- 生成者Oracle SQL Developer Data Modeler 24.3.1.351.0831
--   时间:        2025-09-04 16:48:59 CST
--   站点:      Oracle Database 11g
--   类型:      Oracle Database 11g



-- predefined type, no DDL - MDSYS.SDO_GEOMETRY

-- predefined type, no DDL - XMLTYPE

CREATE TABLE BelongTo 
    ( 
     Drink_ID      VARCHAR2 (20)  NOT NULL , 
     order_OrderId VARCHAR2 (20)  NOT NULL 
    ) 
;

ALTER TABLE BelongTo 
    ADD CONSTRAINT BelongTo_PK PRIMARY KEY ( Drink_ID, order_OrderId ) ;

CREATE TABLE ComposeOf 
    ( 
     Drink_ID           VARCHAR2 (20)  NOT NULL , 
     Ingredient_ID      VARCHAR2 (20)  NOT NULL , 
     QuantityProportion FLOAT (2) 
    ) 
;

ALTER TABLE ComposeOf 
    ADD CONSTRAINT ComposeOf_PK PRIMARY KEY ( Drink_ID, Ingredient_ID ) ;

CREATE TABLE Drink 
    ( 
     DrinkId     VARCHAR2 (20)  NOT NULL , 
     Name        VARCHAR2 (20)  NOT NULL , 
     Price       INTEGER  NOT NULL , 
     Remains     INTEGER  NOT NULL , 
     sale_status VARCHAR2 (20)  NOT NULL , 
     ingredient  VARCHAR2 (100)  NOT NULL 
    ) 
;

ALTER TABLE Drink 
    ADD CONSTRAINT Drink_PK PRIMARY KEY ( DrinkId ) ;

CREATE TABLE Employee 
    ( 
     EmployeeId VARCHAR2 (20)  NOT NULL , 
     Name       VARCHAR2 (20)  NOT NULL , 
     HireDate   DATE , 
     Phone      VARCHAR2 (20) 
    ) 
;

ALTER TABLE Employee 
    ADD CONSTRAINT Employee_PK PRIMARY KEY ( EmployeeId ) ;

CREATE TABLE Ingredient 
    ( 
     IngredientId   VARCHAR2 (20)  NOT NULL , 
     Name           VARCHAR2 (20)  NOT NULL , 
     Quantity       INTEGER  NOT NULL , 
     SiglePrice     FLOAT (2) , 
     AlertThreshold INTEGER  NOT NULL 
    ) 
;

ALTER TABLE Ingredient 
    ADD CONSTRAINT Ingredient_PK PRIMARY KEY ( IngredientId ) ;

CREATE TABLE member 
    ( 
     MemberId      VARCHAR2 (20)  NOT NULL , 
     name          VARCHAR2 (20)  NOT NULL , 
     phone_number  VARCHAR2 (20)  NOT NULL , 
     mail_box      VARCHAR2 (20) , 
     register_date VARCHAR2 (20) , 
     history_order VARCHAR2 (500) 
    ) 
;

ALTER TABLE member 
    ADD CONSTRAINT member_PK PRIMARY KEY ( MemberId ) ;

CREATE TABLE "order" 
    ( 
     OrderId             VARCHAR2 (20)  NOT NULL , 
     time                DATE  NOT NULL , 
     status              VARCHAR2 (20)  NOT NULL , 
     price               INTEGER  NOT NULL , 
     star                INTEGER , 
     maker_id            VARCHAR2 (20)  NOT NULL , 
     BuyerId             VARCHAR2 (20)  NOT NULL , 
     member_MemberId     VARCHAR2 (20)  NOT NULL , 
     Walkin_WalkinId     VARCHAR2 (20) , 
     Employee_EmployeeId VARCHAR2 (20) 
    ) 
;

ALTER TABLE "order" 
    ADD CONSTRAINT order_PK PRIMARY KEY ( OrderId ) ;

CREATE TABLE Walkin 
    ( 
     WalkinId      VARCHAR2 (20)  NOT NULL , 
     name          VARCHAR2 (20)  NOT NULL , 
     phone_number  VARCHAR2 (20)  NOT NULL , 
     history_order VARCHAR2 (500) , 
     Walkin_Date   DATE 
    ) 
;

ALTER TABLE Walkin 
    ADD CONSTRAINT WALK_IN_PK PRIMARY KEY ( WalkinId ) ;

ALTER TABLE BelongTo 
    ADD CONSTRAINT BelongTo_Drink_FK FOREIGN KEY 
    ( 
     Drink_ID
    ) 
    REFERENCES Drink 
    ( 
     DrinkId
    ) 
;

ALTER TABLE BelongTo 
    ADD CONSTRAINT BelongTo_order_FK FOREIGN KEY 
    ( 
     order_OrderId
    ) 
    REFERENCES "order" 
    ( 
     OrderId
    ) 
;

ALTER TABLE ComposeOf 
    ADD CONSTRAINT ComposeOf_Drink_FK FOREIGN KEY 
    ( 
     Drink_ID
    ) 
    REFERENCES Drink 
    ( 
     DrinkId
    ) 
;

ALTER TABLE ComposeOf 
    ADD CONSTRAINT ComposeOf_Ingredient_FK FOREIGN KEY 
    ( 
     Ingredient_ID
    ) 
    REFERENCES Ingredient 
    ( 
     IngredientId
    ) 
;

ALTER TABLE "order" 
    ADD CONSTRAINT order_Employee_FK FOREIGN KEY 
    ( 
     Employee_EmployeeId
    ) 
    REFERENCES Employee 
    ( 
     EmployeeId
    ) 
;

ALTER TABLE "order" 
    ADD CONSTRAINT order_member_FK FOREIGN KEY 
    ( 
     member_MemberId
    ) 
    REFERENCES member 
    ( 
     MemberId
    ) 
;

ALTER TABLE "order" 
    ADD CONSTRAINT order_Walkin_FK FOREIGN KEY 
    ( 
     Walkin_WalkinId
    ) 
    REFERENCES Walkin 
    ( 
     WalkinId
    ) 
;



-- Oracle SQL Developer Data Modeler 概要报告: 
-- 
-- CREATE TABLE                             8
-- CREATE INDEX                             0
-- ALTER TABLE                             15
-- CREATE VIEW                              0
-- ALTER VIEW                               0
-- CREATE PACKAGE                           0
-- CREATE PACKAGE BODY                      0
-- CREATE PROCEDURE                         0
-- CREATE FUNCTION                          0
-- CREATE TRIGGER                           0
-- ALTER TRIGGER                            0
-- CREATE COLLECTION TYPE                   0
-- CREATE STRUCTURED TYPE                   0
-- CREATE STRUCTURED TYPE BODY              0
-- CREATE CLUSTER                           0
-- CREATE CONTEXT                           0
-- CREATE DATABASE                          0
-- CREATE DIMENSION                         0
-- CREATE DIRECTORY                         0
-- CREATE DISK GROUP                        0
-- CREATE ROLE                              0
-- CREATE ROLLBACK SEGMENT                  0
-- CREATE SEQUENCE                          0
-- CREATE MATERIALIZED VIEW                 0
-- CREATE MATERIALIZED VIEW LOG             0
-- CREATE SYNONYM                           0
-- CREATE TABLESPACE                        0
-- CREATE USER                              0
-- 
-- DROP TABLESPACE                          0
-- DROP DATABASE                            0
-- 
-- REDACTION POLICY                         0
-- 
-- ORDS DROP SCHEMA                         0
-- ORDS ENABLE SCHEMA                       0
-- ORDS ENABLE OBJECT                       0
-- 
-- ERRORS                                   0
-- WARNINGS                                 0
