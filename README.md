# Documentacion de Sigma v2

- [Base Endpoint](#base-endpoint)
- [Autenticacion](#autenticacion)
- [Seguridad](#seguridad-token)
- [OSINT Endpoints](#osint-endpoints)

## Base Endpoint:
```https://sigma-search.io/api/v2```

## Autenticacion:
1. Ir al developer dashboard y copiar tu Token
2. La autenticacion es via header `sigma-key` 

| Header | Token |
| ------------- | -------------
sigma-key |c1c611c1-0534-41ac-9537-9de570lpc647 

## Seguridad Token:
1. Para generar un nuevo Token hace click donde dice `Generar nueva API Key` y vas a obtener un nuevo Token

# OSINT Endpoints:
Los endpoints OSINT permiten obtener información open source sobre personas.

- Free plan
    - [Peru resolver](#peru-resolver-free)
- Standard plan
    - [DNI resolver](#dni-resolver-standard-medium-profesional)
    - [DNI Celular resolver](#dni-celular-resolver-standard-medium-profesional)
- Medium plan
    - [Patente resolver](#patente-resolver-medium-profesional)
    - [Patente DNI resolver](#patente-dni-resolver-medium-profesional)
    - [Data breach resolver](#data-breach-resolver-medium-profesional)
- Profesional plan
    - [DNI Profesional resolver](#dni-profesional-resolver-profesional)
    - [Celular resolver](#celular-resolver-profesional)
    - [Direccion resolver](#direccion-resolver-profesional)
    - [Nombre resolver](#nombre-resolver-profesional)
    - [Movistar resolver](#movistar-resolver-profesional)
    - [Magic resolver](#magic-resolver-profesional)

## Peru Resolver (Free)
El Peru resolver permite obtener información sobre una persona a través de su celular o numero de identificación.

| Plan | Rate-limit |
| ---- | ---------- |
| Free | 10 consultas / 5 min |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/free/osint/peru/resolver/celular_dni` | https://sigma-search.io/api/v2/free/osint/peru/resolver/celular_dni |

## Request Data
| Metodo | Content-Type | Data |
| ------ | ------------ | ---- |
| **POST** | `application/JSON` | `{"dato": str}` |

## Respuesta 200 OK
```json
{
    "sigma_db": [
        {
            "documento": "12345678",
            "fuente": "Sigma DB 2021",
            "numero": "51368280",
            "tipo": "1"
        },
        {
            "documento": "12345678",
            "fuente": "Sigma DB 2021",
            "numero": "15315731",
            "tipo": "1"
        }
]
```

## DNI Resolver (Standard, medium, profesional)
El DNI resolver permite obtener información sobre una persona a través de su DNI.

| Plan | Rate-limit |
| ---- | ---------- |
| Standard | 15 consultas / 30 min |
| Medium | 100 consultas / 5 min |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/resolver/dni` | https://sigma-search.io/api/v2/standard/osint/argentina/resolver/dni |

## Request Data
| Metodo | Content-Type | Data |
| ------ | ------------ | ---- |
| **POST** | `application/JSON` | `{"dni": str}` |

## Respuesta 200 OK
```json
{
    "doc": "12345678",
    "apellido": "BIANCIOTTO",
    "nombres": "ALDO RUBEN",
    "calle": "CHICLANA 533",
    "seccion": "79 - MORENO",
    "circuito": "663 - MORENO / PASO",
    "tipo_doc": "DNI-EA",
    "localidad": "MORENO",
    "provincia": "Buenos Aires",
    "codigo_postal": "1744"
}
```

## DNI-Celular Resolver (Standard, medium, profesional)
El DNI-Celular resolver permite obtener los números de celular de una persona a través de su DNI.

| Plan | Rate-limit |
| ---- | ---------- |
| Standard | 15 consultas / 30 min |
| Medium | 100 consultas / 5 min |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/resolver/dni_celular` | https://sigma-search.io/api/v2/standard/osint/argentina/resolver/dni_celular |

## Request Data
| Metodo | Content-Type | Data |
| ------ | ------------ | ---- |
| **POST** | `application/JSON` | `{"dni": str}` |

## Respuesta 200 OK
```json
[
  {
        "numero": "1160257687",
        "doc": "12345678",
        "nombre": "FELICIANO CHICLANA 533 01508",
        "localidad": "MORENO",
        "provincia": null,
        "codigo_postal": "1744",
        "empresa": "claro"
    }
]
```

## Patente Resolver (Medium, profesional)
El Patente resolver permite obtener los datos de un vehiculo a través de su patente.

| Plan | Rate-limit |
| ---- | ---------- |
| Medium | 100 consultas / 5 min |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/resolver/patente` | https://sigma-search.io/api/v2/medium/osint/argentina/resolver/patente |

## Request Data
| Metodo | Content-Type | Data |
| ------ | ------------ | ---- |
| **POST** | `application/JSON` | `{"patente": str}` |

## Respuesta 200 OK
```json
[
    {
        "patente": "GAY001",
        "documento": "24546048",
        "vehiculo": "STRADA ADVENTURE 1.8MPI 8V C Y M",
        "marca": "FIAT",
        "anio": "2007",
        "titular": "RIVERO NARA LUZ",
        "porcentaje": "100",
        "calle": "DIAGONAL 73 E/3 Y 4",
        "altura": "834",
        "piso": null,
        "depto": null,
        "codigo_postal": "1900",
        "localidad": "LA PLATA.",
        "transferencia": "11/2/2011"
    }
]
```

## Patente-DNI Resolver (Medium, profesional)
El Patente-DNI resolver permite obtener los datos de un vehiculo a través del DNI del titular.

| Plan | Rate-limit |
| ---- | ---------- |
| Medium | 100 consultas / 5 min |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/resolver/patente_dni` | https://sigma-search.io/api/v2/medium/osint/argentina/resolver/patente_dni |

## Request Data
| Metodo | Content-Type | Data |
| ------ | ------------ | ---- |
| **POST** | `application/JSON` | `{"dni": str}` |

## Respuesta 200 OK
```json
[
    {
        "patente": "GAY001",
        "documento": "24546048",
        "vehiculo": "STRADA ADVENTURE 1.8MPI 8V C Y M",
        "marca": "FIAT",
        "anio": "2007",
        "titular": "RIVERO NARA LUZ",
        "porcentaje": "100",
        "calle": "DIAGONAL 73 E/3 Y 4",
        "altura": "834",
        "piso": null,
        "depto": null,
        "codigo_postal": "1900",
        "localidad": "LA PLATA.",
        "transferencia": "11/2/2011"
    }
]
```

## Data breach Resolver (Medium, profesional)
Devuelve datos leakeados de un dominio o email determinada.

| Plan | Rate-limit |
| ---- | ---------- |
| Medium | 100 consultas / 5 min |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/search_engine/data_breach` | https://sigma-search.io/api/v2/medium/osint/argentina/search_engine/data_breach |

## Request Data
| Metodo | Content-Type | Data |
| ------ | ------------ | ---- |
| **POST** | `application/JSON` | `{"query": str}` |

## Respuesta 200 OK
```json
[
    {
        "usuario": "cr**ca@email.msn.com",
        "password": "*****"
    },
    {
        "usuario": "cr**ca@gmx.net",
        "password": "*****"
    }
]
```

## DNI Profesional Resolver (Profesional)
El DNI Profesional resolver permite obtener los datos de una persona a través de su DNI, este endpoint incluye más información exclusiva.

| Plan | Rate-limit |
| ---- | ---------- |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/resolver/dni_two` | https://sigma-search.io/api/v2/profesional/osint/argentina/resolver/dni_two |

## Request Data
En la data se debe incluir el genero de la persona, separando el DNI con `:`, donde el genero es `Masculino` o `Femenino`
| Metodo | Content-Type | Data | Ejemplo data |
| ------ | ------------ | ---- | ------------ |
| **POST** | `application/JSON` | `{"dato": str:str}` | `{"dato": "12345678:Masculino"}`

## Respuesta 200 OK
```json
{
    "emision": ""
    "apellido": "BIANCIOTTO",
    "nombres": "ALDO RUBEN",
    "cuil": ""
    "calle": "CHICLANA",
    "numero": "533",
    "piso": ""
    "departamento": ""
    "barrio": ""
    "monoblock": ""
    "ciudad": "MORENO",
    "municipio": "MORENO",
    "provincia": "BUENOS_AIRES",
    "pais": "ARGENTINA",
    "foto": ""
    "tramite": ""
    "documento": "12345678",
    "fallecido": "Sin Aviso de Fallecimiento",
    "codigo_postal": "1744",
    "fecha_nacimiento": "1956-08-19",
    "cobertura": [
        {
            "cobertura": "INSTITUTO NACIONAL DE SERVICIOS SOCIALES PARA JUBILADOS Y PENSIONADOS",
            "nombre": "500807",
            "dni": "12345678",
            "sexo": "Masculino"
        }
    ],
    "edad": 66
}
```

## Celular Resolver (Profesional)
El celular resolver devuelve información sobre los titulares de un número de telefono.

| Plan | Rate-limit |
| ---- | ---------- |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/resolver/celular` | https://sigma-search.io/api/v2/profesional/osint/argentina/resolver/celular |

## Request Data
| Metodo | Content-Type | Data |
| ------ | ------------ | ---- |
| **POST** | `application/JSON` | `{"num": str}` |

## Respuesta 200 OK
```json
[
    {
        "celular": "1160257687",
        "documento": "12345678",
        "nombre": "BIANCIOTTO ALDO RUBEN",
        "direccion": "FELICIANO CHICLANA 533 01508",
        "localidad": "MORENO",
        "provincia": null,
        "codigo_postal": "1744",
        "empresa": "claro"
    }
]
```

## Direccion Resolver (Profesional)
El direccion resolver permite obtener información sobre todos los vecinos de una determinada calle.

| Plan | Rate-limit |
| ---- | ---------- |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/resolver/direccion` | https://sigma-search.io/api/v2/profesional/osint/argentina/resolver/direccion |

## Request Data
| Metodo | Content-Type | Data |
| ------ | ------------ | ---- |
| **POST** | `application/JSON` | `{"direccion": str}` |

## Respuesta 200 OK
```json
[
    {
        "numero": "3516710308",
        "doc": "16744292",
        "nombre": "Fabian Anselmo Suppo",
        "direccion": "Niceto Vega Barrio Bel 2623",
        "localidad": "Cordoba",
        "provincia": "Cordoba",
        "codigo_postal": "5012",
        "empresa": "movistar"
    }
]
```

## Nombre Resolver (Profesional)
El nombre resolver permite buscar personas por su nombre, además, se aceptan filtros por provincia, localidad, y rango de edad.

| Plan | Rate-limit |
| ---- | ---------- |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/resolver/nombre` | https://sigma-search.io/api/v2/profesional/osint/argentina/resolver/nombre |

## Request Data
| Metodo | Content-Type | Data | Opcional |
| ------ | ------------ | ---- | -------- |
| **POST** | `application/JSON` | `{"nombre": str}` | `{"provincia_nombre": str, "localidad": str, "edad_desde": int, "edad_hasta": int}` |

## Respuesta 200 OK
```json
[
    {
        "nombre": "PEREZ PEREZ ANGEL CARLOS",
        "documento": "27-31931905-6",
        "provincia": "Tierra del Fuego"
    }
]
```

## Movistar Resolver (Profesional)
El Movistar resolver permite obtener el email de una persona a través de su número celular perteneciente a Movistar.

| Plan | Rate-limit |
| ---- | ---------- |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/resolver/movistar` | https://sigma-search.io/api/v2/profesional/osint/argentina/resolver/movistar |

## Request Data
| Metodo | Content-Type | Data |
| ------ | ------------ | ---- |
| **POST** | `application/JSON` | `{"num": str}` |

## Respuesta 200 OK
```json
{
    "num": "0000000000",
    "email": "example@gmail.com"
}
```

## Magic Resolver (Profesional)
El Magic resolver permite buscar información de una persona a través de su número (de una DB diferente), CVU o email. 

| Plan | Rate-limit |
| ---- | ---------- |
| Profesional | Sin rate-limit |

## Endpoint URL
| Path | Ejemplo |
| ---- | ------- |
| `/{plan}/osint/argentina/resolver/magic` | https://sigma-search.io/api/v2/profesional/osint/argentina/resolver/magic |

## Request Data
| Metodo | Content-Type | Data |
| ------ | ------------ | ---- |
| **POST** | `application/JSON` | `{"dato": str, "tipo": str}`

| Tipo | Descripcion |
| ---- | ----------- |
| `buscar_celular` | Busca datos de un celular |
| `buscar_email` | Buscar datos de un email |
| `buscar_cbu_alias` | Buscar datos de un CVU/CBU o alias |

## Respuesta 200 OK (Tipo: buscar_celular)
```json
{
    "nombre": "Silvana Esther",
    "apellido": "Mingorance",
    "email": "si****@hotmail.com",
    "numero": "1158490291"
}
```

## Respuesta 200 OK (Tipo: buscar_email)
```json
{
    "nombre": "Emanuel Matias",
    "apellido": "Andreocci",
    "email": "quilmes@gmail.com"
}
```

## Respuesta 200 OK (Tipo: buscar_cbu_alias)
```json
{
    "nombre": "Garcia Luis Adrian",
    "cuit": "20-22457540-9",
    "banco": "Banco de la Nacion Argentina",
    "cbu": "0110018130001812348815",
    "cuenta_tipo": "Caja de ahorro"
}
```
