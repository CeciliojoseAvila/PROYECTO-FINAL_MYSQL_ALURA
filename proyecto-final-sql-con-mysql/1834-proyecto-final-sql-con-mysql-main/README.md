# COMANDOS PARA ACCEDER PERMISOS A USURIOS ADMIN Y NORMAL CON LIMITES:
Este repositorio contiene el proyecto final de SQL con MySQL de Alura en español.
CREATE USER 'admin03'@'localhost' IDENTIFIED BY 'admin03';
GRANT ALL PRIVILEGES ON *.* TO 'admin03'@'localhost' WITH GRANT OPTION;
-- CREACION DE USUARIOS NORMALES, CON PRIVILEGIOS: create, select, update, INSERT, alter, 
-- create TEMPORARY TABLES, execute, lock table.
CREATE USER 'usuario02'@'localhost' IDENTIFIED BY 'usuario02';
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE TEMPORARY TABLES, LOCK TABLES,
EXECUTE ON *.* TO 'usuario02'@'localhost';
-- USUARIO CON PRIVILEGIOS PARA BACK-UP:
CREATE USER 'backup01'@'localhost' IDENTIFIED BY 'backup01';
GRANT SELECT, RELOAD, LOCK TABLES, REPLICATION CLIENT ON *.* TO 'backup01'@'localhost';

-- USUARIO CON PRIVILEGIOS PARA BACK-UP COMO ADMIN:
CREATE USER 'admingenerico'@'%' IDENTIFIED BY 'admingenerico';
GRANT ALL PRIVILEGES ON *.* TO 'admingenerico'@'%' WITH GRANT OPTION;

--  También, puedes limitar el acceso a las tablas, 
-- estableciendo permisos sobre las operaciones que se pueden realizar sobre ellas:
CREATE USER 'user05'@'%' IDENTIFIED BY 'user05';
GRANT SELECT, INSERT, UPDATE, DELETE ON jugos_ventas.facturas TO 'user05'@'%';
GRANT SELECT ON jugos_ventas.tabla_de_vendedores TO 'user05'@'%';

/* crear una conexion de usuario limitado*/
CREATE USER 'userio05'@'%' IDENTIFIED BY 'userio05';
GRANT SELECT, INSERT, UPDATE, DELETE ON jugos_ventas.facturas TO 'userio05'@'%';
GRANT SELECT ON jugos_ventas.tabla_de_vendedores TO 'userio05'@'%';

-- intentar agregar datos y botará error:
INSERT INTO `jugos_ventas`.`tabla_de_vendedores`
(`MATRICULA`,
`NOMBRE`,
`PORCENTAJE_COMISION`,
`FECHA_ADMISION`,
`VACACIONES`,
`BARRIO`)
VALUES
('256',
'Jose García',
0.15,
'20190303',
0,
'Oblatos');

/*
9) Existe un comando para verificar los usuarios existentes:

SELECT * FROM mysql.user;
10) Adicionalmente, hay otro comando que muestra los accesos de un usuario, por ejemplo:

SHOW GRANTS FOR 'user02'@'localhost';
11) Finalmente, el comando REVOKE ALL retira los privilegios de acceso del usuario 
especificado:

REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'user02'@'localhost';
*/
SELECT * FROM mysql.user;
