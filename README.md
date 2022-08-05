# Documentacion de Sigma v1

## Endpoint principal:
```sigma-search.io```

## Autenticacion:
1. Ir al developer dashboard y copiar tu Token
2. La autenticacion es via header `sigma-key` 

| Header | Token |
| ------------- | -------------
sigma-key |c1c611c1-0534-41ac-9537-9de570lpc647 

## Seguridad Token:
1. Para generar un nuevo Token hace click donde dice `Generar nueva API Key` y vas a obtener un nuevo Token

# Endpoints:

## Profesional
| Endpoint | Metodo | Tipo dato | Data Post | Respuesta 200 OK | Respuesta 400 | Rate Limit
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
/api/sigma/profesional/movistar-resolver | POST | JSON | num: str | num: str, email: str | {err: true, error: "No se encontro el numero en nuestra DB Movistar"} | Ilimitado
/api/sigma/profesional/patente-resolver | POST | JSON | patente: str | patente: str, documento: str, vehiculo: str, marca: str, anio: str, titular: str, porcentaje: str, calle: str, altura: str, piso: str, depto: str, codigo_postal: str, localidad: str, transferencia: str | {"error": "No se encontro la patente abc123 en nuestras base de datos."} | Ilimitado
/api/sigma/profesional/patente-dni-resolver | POST | JSON | dni:str | patente: str, documento: str, vehiculo: str, marca: str, anio: str, titular: str, porcentaje: str, calle: str, altura: str, piso: str, depto: str, codigo_postal: str, localidad: str, transferencia: str | {"error":"El dni 12345678 no se encontro en nuestra base de datos de patentes."} | Ilimitado
/api/sigma/profesional/dni-resolver | POST | JSON | dni:str | doc: str, apellido: str, nombres: str, calle: str, seccion: str, circuito: str, tipo_doc: str, localidad: str, provincia: str, codigo_postal: str | {"error":"El dni 12345678 no se encontro en nuestra base de datos de patentes."} | Ilimitado
/api/sigma/profesional/dni-number-resolver | POST | JSON | dni:str | numero: str, doc: str, nombre: str, localidad: str, provincia: str, codigo_postal: str, empresa: str | {"error":"No se encontro el dni dnifake123 en nuestras base de datos."} | Ilimitado
/api/sigma/profesional/dni-resolver-2 | POST | JSON | dni:str | tipoDocumento: str, nroDocumento: str, apellido: str, nombre: str, sexo: str, fechaNacimiento:str, estadoCivil: str, cobertura: list => tipoCobertura: str, nombreObraSocial: str, rnos: str, vigenciaDesde: str, fechaActualizacion:str | {"error":"No se encontro el dni dnifake123 en nuestras base de datos."} | Ilimitado
/api/sigma/profesional/num_resolver | POST | JSON | num:str | numero: str, doc: str, nombre: str, localidad: str, provincia: str, codigo_postal: str, empresa: str | {"error":"No se encontro el numero 0101010101 en nuestras base de datos."} | Ilimitado

## Medium
| Endpoint | Metodo | Tipo dato | Data Post | Respuesta 200 OK | Respuesta 400 | Rate Limit
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
/api/sigma/medium/patente-resolver-medium | POST | JSON | patente: str | patente: str, documento: str, vehiculo: str, marca: str, anio: str, titular: str, porcentaje: str, calle: str, altura: str, piso: str, depto: str, codigo_postal: str, localidad: str, transferencia: str | {"error":"No se encontro la patente fakepatente123 en nuestras base de datos."} | 100 consultas / 5 min
/api/sigma/medium/patente-resolver-dni-medium | POST | JSON | dni:str | patente: str, documento: str, vehiculo: str, marca: str, anio: str, titular: str, porcentaje: str, calle: str, altura: str, piso: str, depto: str, codigo_postal: str, localidad: str, transferencia: str | {"error":"No se encontro la patente fakepatente123 en nuestras base de datos."} | 100 consultas / 5 min
/api/sigma/medium/dni-number-resolver-medium | POST | JSON | number:str | doc: str, apellido: str, nombres: str, calle: str, seccion: str, circuito: str, tipo_doc: str, localidad: str, provincia: str, codigo_postal: str | {"error":"No se encontro el dni 12345678 en nuestras base de datos."} | 100 consultas / 5 min
/api/sigma/medium/dni-resolver-medium | POST | JSON | dni:str | numero: str, doc: str, nombre: str, localidad: str, provincia: str, codigo_postal: str, empresa: str | dict: error | 100 consultas / 5 min

## Standard
| Endpoint | Metodo | Tipo dato | Data Post | Respuesta 200 OK | Respuesta 400 | Rate Limit
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
/api/sigma/standard/dni-number-resolver-standard| POST | JSON | dni:str | doc: str, apellido: str, nombres: str, calle: str, seccion: str, circuito: str, tipo_doc: str, localidad: str, provincia: str, codigo_postal: str | {"error":"No se encontro el dni 12345678 en nuestras base de datos."} | 15 consultas / 30 minutos
/api/sigma/standard/dni-resolver-standard | POST | JSON | dni:str | numero: str, doc: str, nombre: str, localidad: str, provincia: str, codigo_postal: str, empresa: str | {"error":"No se encontro el dni 12345678 en nuestras base de datos."} | 15 consultas / 30 minutos

## Free
| Endpoint | Metodo | Tipo dato | Data Post | Respuesta 200 OK | Respuesta 400 | Rate Limit
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
/api/sigma/free/peru-resolver-telefonos | POST | JSON | dict:sigma_db => documento:str, fuente:str, numero:str, tipo:str | {"error": "No se encontro el dato fakedni123 en nuestras base de datos."} | 10 consultas / 5 min 
