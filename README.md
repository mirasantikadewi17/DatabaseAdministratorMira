CREATE SCHEMA app;

CREATE TABLE app.produk (
    no SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL);

INSERT INTO app.produk (name)
VALUES
	('Hydro Coco 250ml'),
    ('Hydro Coco 330ml'),
    ('Hydro Coco 500ml'),
    ('Hydro Coco 1 liter'),
    ('Hydro Coco Vita-D 330ml'),
    ('Milna Biskuit Bayi Original'),
    ('Milna Biskuit Bayi Beras Merah'),
    ('Milna Biskuit Bayi Kacang Hijau'),
    ('Milna Biskuit Bayi Jeruk'), 
	('Milna Biskuit Bayi Pisang'), 
	('Milna Biskuit Bayi Apel'), 
	('Milna Biskuit Bayi Apel Jeruk'), 
	('Milna Bubur Bayi Beras Merah Untuk 6 - 12 Bulan'), 
	('Milna Bubur Bayi Pisang Untuk 6 - 12 Bulan'), 
	('Milna Bubur Bayi Sup Ayam Wortel Untuk 6 - 12 Bulan'), 
	('Milna Bubur Bayi Sup Daging Brokoli Untuk 6 - 12 Bulan'), 
	('Milna Bubur Bayi Tim Hati Ayam Bayam Untuk 6 - 12 Bulan'), 
	('Milna Bubur Bayi Ayam Jagung Manis Untuk 8 - 12 Bulan'), 
	('Milna Bubur Bayi Daging Kacang Polong Untuk 8 - 12 Bulan'), 
	('Milna Bubur Bayi Hati Ayam Brokoli Untuk 8 - 12 Bulan'), 
	('Milna Bubur Organik Pisang'), 
	('Milna Bubur Organik Kacang Hijau'), 
	('Milna Bubur Organik Beras Merah'), 
	('Milna Bubur Organik Multigrain'), 
	('Milna Bubur Bayi WGAIN Ayam Kacang Polong'), 
	('Milna Bubur Bayi WGAIN Ayam Wortel Brokoli'), 
	('Milna Bubur Bayi WGAIN Ayam Manis Teriyaki'), 
	('Milna Bubur Bayi WGAIN Ayam Bayam'), 
	('Milna Goodmil Peach Stroberi Jeruk'), 
	('Milna Goodmil Wortel Labu'), 
	('Milna Goodmil Beras Merah Semur Ayam'), 
	('Milna Goodmil Beras Merah Pisang'), 
	('Milna Goodmil Beras Merah Ayam'), 
	('Milna Goodmil Hypoallergenic Beras Merah'), 
	('Milna Nature Delight Apel Peach'), 
	('Milna Nature Delight Apel Labu Wortel'), 
	('Milna Nature Delight Apel Pisang Stroberi'), 
	('Milna Biskuit Bayi Finger'), 
	('Milna Nature Puffs Organic Pisang'), 
	('Milna Nature Puffs Organic Keju'), 
	('Milna Nature Puffs Organic Apel & Mix Berries'), 
	('Milna Rice Crackers Apple Orange'), 
	('Milna Rice Crackers Banana Berries'), 
	('Milna Rice Crackers Sweet Potato Carrot'), 
	('Nutrive Benecol Blackcurrant'), 
	('Nutrive Benecol Strawberry'), 
	('Nutrive Benecol Orange'), 
	('Nutrive Benecol Lychee'), 
	('Entrasol Active Vanilla latte'), 
	('Entrasol Active Mochaccino'), 
	('Entrasol Active Chocolate'), 
	('Entrasol Gold Original'), 
	('Entrasol Gold Chocolate'), 
	('Entrasol Gold Vanilla'), 
	('Entrasol UHT Vanilla Latte'), 
	('Entrasol UHT Chocolate'), 
	('Entrasol Cereal Vanilla Vegie'), 
	('Entrasol Cereal Chocolate'), 
	('Entrasol Platinum Vanilla'), 
	('Entrasol Platinum Chocolate');
	
CREATE USER backend_user WITH PASSWORD 'password';
GRANT CONNECT ON DATABASE app TO backend_user;
GRANT USAGE ON SCHEMA app TO backend_user;
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA app TO backend_user;

CREATE INDEX idx_produk_name ON app.produk (name);

SELECT * FROM app.produk;

#Table_Shipping
CREATE TABLE app.Shipping (
    ShippingID SERIAL PRIMARY KEY,
    ProductName VARCHAR(255),
    Qty INTEGER,
    Unit VARCHAR(50),
    StoreDestination VARCHAR(255),
    StoreAddress VARCHAR(255),
    Operator VARCHAR(255),
    ShippingVehicle VARCHAR(255),
    NoPolisi VARCHAR(20),
    ShippingDriver VARCHAR(255),
    ShippingCoDriver VARCHAR(255),
    SendingTime TIMESTAMP,
    DeliveredTime TIMESTAMP,
    ReceivedBy VARCHAR(255));

INSERT INTO app.Shipping (ProductName, Qty, Unit, StoreDestination, StoreAddress, Operator, ShippingVehicle, NoPolisi, ShippingDriver, ShippingCoDriver, SendingTime, DeliveredTime, ReceivedBy)
VALUES
    ('Hydro Coco 250ml', 5, 'box', 'Apotek Agus Sari', 'Jln Angga Jaya no 21', 'Ahmad Agus', 'Box A001', 'B 1234 GA', 'Dimas Ahmad', 'Andi Wahyu', '2023-05-01 10:00', '2023-05-01 13:30', 'Dian Ayu'), 
	('Hydro Coco Vita-D 330ml', 5, 'box', 'Apotek Agus Sari', 'Jln Angga Jaya no 21', 'Ahmad Agus', 'Box A001', 'B 1234 GA', 'Dimas Ahmad', 'Andi Wahyu', '2023-05-01 10:00', '2023-05-01 13:30', 'Dian Ayu'),
    ('Milna Biskuit Bayi Apel', 10, 'box', 'Apotek Agus Sari', 'Jln Angga Jaya no 21', 'Ahmad Agus', 'Box A001', 'B 1234 GA', 'Dimas Ahmad', 'Andi Wahyu', '2023-05-01 10:00', '2023-05-01 13:30', 'Dian Ayu'),
	('Hydro Coco 250ml', 3, 'box', 'Toko Maju Bersama', 'Jln Agus Salim no 22', 'Ahmad Agus', 'Box A002', 'B 3214 JS', 'Hari Saputra', 'Dadang Bima', '2023-05-01 11:00', '2023-05-01 13:00', 'Eriawan'), 
	('Hydro Coco 330ml', 2, 'box', 'Toko Maju Bersama', 'Jln Agus Salim no 22', 'Ahmad Agus', 'Box A002', 'B 3214 JS', 'Hari Saputra', 'Dadang Bima', '2023-05-01 11:00', '2023-05-01 13:00', 'Eriawan'), 
	('Entrasol Gold Original', 8, 'box', 'Toko Maju Bersama', 'Jln Agus Salim no 22', 'Ahmad Agus', 'Box A002', 'B 3214 JS', 'Hari Saputra', 'Dadang Bima', '2023-05-01 11:00', '2023-05-01 13:00', 'Eriawan'), 
	('Milna Nature Delight Apel Peach', 10, 'box', 'Toko Anak Sehat', 'Jln Imam Bonjol no 33', 'Fitrianto', 'Box A001', 'B 1234 GA', 'Ginanjar', 'Hari Saputra', '2023-05-02 09:00', '2023-05-02 12:00', 'Aji'), 
	('Milna Nature Delight Labu Wortel', 5, 'box', 'Toko Anak Sehat', 'Jln Imam Bonjol no 33', 'Fitrianto', 'Box A001', 'B 1234 GA', 'Ginanjar', 'Hari Saputra', '2023-05-02 09:00', '2023-05-02 12:00', 'Aji'), 
	('Milna Rice Crackers Apple Orange', 12, 'box', 'Toko Anak Sehat', 'Jln Imam Bonjol no 33', 'Fitrianto', 'Box A001', 'B 1234 GA', 'Ginanjar', 'Hari Saputra', '2023-05-02 09:00', '2023-05-02 12:00', 'Aji'), 
	('Milna Bubur Organik Multigrain', 10, 'box', 'Toko Anak Sehat', 'Jln Imam Bonjol no 33', 'Fitrianto', 'Box A001', 'B 1234 GA', 'Ginanjar', 'Hari Saputra', '2023-05-02 09:00', '2023-05-02 12:00', 'Aji'), 
	('Entrasol Active Vanilla Latte', 5, 'box', 'Apotek Agung', 'Pasar Senen no 301', 'Fitrianto', 'Box A001', 'B 1234 GA', 'Ginanjar', 'Hari Saputra', '2023-05-02 09:00', '2023-05-02 14:00', 'Jamal'), 
	('Entrasol Gold Original', 4, 'box', 'Apotek Agung', 'Pasar Senen no 301', 'Fitrianto', 'Box A001', 'B 1234 GA', 'Ginanjar', 'Hari Saputra', '2023-05-02 09:00', '2023-05-02 14:00', 'Jamal'), 
	('Entrasol Gold Chocolate', 6, 'box', 'Apotek Agung', 'Pasar Senen no 301', 'Fitrianto', 'Box A001', 'B 1234 GA', 'Ginanjar', 'Hari Saputra', '2023-05-02 09:00', '2023-05-02 14:00', 'Jamal');

SELECT ShippingDriver, COUNT(*) AS TotalShipments
FROM app.Shipping
WHERE EXTRACT(MONTH FROM SendingTime) = 5 AND EXTRACT(YEAR FROM SendingTime) = 2023
GROUP BY ShippingDriver
ORDER BY TotalShipments DESC
LIMIT 2;

SELECT ProductName, SUM(Qty) AS TotalQuantity
FROM app.Shipping
WHERE EXTRACT(MONTH FROM SendingTime) = 5 AND EXTRACT(YEAR FROM SendingTime) = 2023
GROUP BY ProductName
ORDER BY TotalQuantity DESC
LIMIT 10;

SELECT *
FROM app.Shipping
WHERE DeliveredTime IS NULL;

CREATE OR REPLACE FUNCTION app.GenerateShipmentID() RETURNS VARCHAR AS $$
DECLARE
    shipment_id VARCHAR;
BEGIN
    SELECT TO_CHAR(CURRENT_TIMESTAMP, 'YYMMDD') || LPAD(COALESCE(MAX(SUBSTRING(ShippingID::VARCHAR, 7)::INTEGER), 0) + 1, 3, '0') INTO shipment_id
    FROM app.Shipping
    WHERE SendingTime::DATE = CURRENT_DATE;
    
    RETURN shipment_id;
END;
$$ LANGUAGE plpgsql; 

CREATE SCHEMA IF NOT EXISTS app; 

CREATE OR REPLACE PROCEDURE app.CreateShipment(
    IN p_ProductName VARCHAR,
    IN p_Qty INTEGER,
    IN p_Unit VARCHAR,
    IN p_StoreDestination VARCHAR,
    IN p_StoreAddress VARCHAR,
    IN p_Operator VARCHAR,
    IN p_ShippingVehicle VARCHAR,
    IN p_NoPolisi VARCHAR,
    IN p_ShippingDriver VARCHAR,
    IN p_ShippingCoDriver VARCHAR,
    IN p_ReceivedBy VARCHAR
)
AS $$
BEGIN
    INSERT INTO app.Shipping (
        ShippingID, ProductName, Qty, Unit, StoreDestination, StoreAddress, Operator, ShippingVehicle, NoPolisi,
        ShippingDriver, ShippingCoDriver, SendingTime, ReceivedBy
    )
    VALUES (
        GenerateShipmentID(), p_ProductName, p_Qty, p_Unit, p_StoreDestination, p_StoreAddress, p_Operator,
        p_ShippingVehicle, p_NoPolisi, p_ShippingDriver, p_ShippingCoDriver, CURRENT_TIMESTAMP, p_ReceivedBy
    );
END;
$$ LANGUAGE plpgsql;

CREATE OR REPLACE PROCEDURE app.AddProductToShipment(
    IN p_ShippingID VARCHAR,
    IN p_ProductName VARCHAR,
    IN p_Qty INTEGER,
    IN p_Unit VARCHAR
)
AS $$
BEGIN
    INSERT INTO app.Shipping (
        ShippingID, ProductName, Qty, Unit, SendingTime
    )
    VALUES (
        p_ShippingID, p_ProductName, p_Qty, p_Unit, CURRENT_TIMESTAMP
    );
END;
$$ LANGUAGE plpgsql;

CREATE EXTENSION pgagent;


SELECT * FROM app.Shipping;
