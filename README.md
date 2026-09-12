# Pokemon del Dia

Script de automatizacion en Python que obtiene los datos de un Pokemon aleatorio desde la API publica de PokeAPI, los almacena en un archivo Excel y envia dicho archivo por correo electronico al destinatario configurado.

---

## Tabla de contenidos

- [Descripcion general](#descripcion-general)
- [Requisitos](#requisitos)
- [Instalacion](#instalacion)
- [Configuracion](#configuracion)
- [Uso](#uso)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Notas de seguridad](#notas-de-seguridad)

---

## Descripcion general

El script ejecuta de forma secuencial las siguientes tres operaciones:

1. Realiza una peticion a la API de [PokeAPI](https://pokeapi.co/) y obtiene los datos de un Pokemon seleccionado aleatoriamente (nombre, ID, altura, peso y tipo).
2. Exporta esos datos a un archivo Excel con el nombre `pokemon_del_dia.xlsx`.
3. Envia el archivo Excel como adjunto a una direccion de correo electronico mediante el servidor SMTP de Gmail.

---

## Requisitos

- Python 3.8 o superior
- Una cuenta de Gmail con verificacion en dos pasos activada
- Una contraseña de aplicacion generada desde la cuenta de Google
- Una cuenta de Outlook
- Un client_secret y un client_id proporcionado por Microsft

Dependencias de Python:

```
pandas
requests
openpyxl
msal
```

---

## Instalacion

1. Clona el repositorio:

```bash
git clone https://github.com/tu_usuario/pokemon-del-dia.git
cd pokemon-del-dia
```

2. Instala las dependencias:

```bash
pip install pandas requests openpyxl
```

3. Copia el archivo de variables de entorno de ejemplo:

```bash
cp .env.example .env
```

---

## Configuracion

Edita el archivo `.env` con tus credenciales reales:

```env
CORREO_EMISOR="tu_correo@gmail.com"
CONTRASENA_CORREO="tu_contrasena_de_aplicacion"
CORREO_RECEPTOR="destinatario@gmail.com"
```

> **Importante:** El campo `CONTRASENA_CORREO` debe contener una contrasena de aplicacion de Google, no la contrasena habitual de tu cuenta. Puedes generarla en [myaccount.google.com/apppasswords](https://myaccount.google.com/apppasswords). Para ello, es necesario tener la verificacion en dos pasos activada.

Si prefieres no usar un archivo `.env`, puedes exportar las variables directamente en tu terminal antes de ejecutar el script:

```bash
export CORREO_EMISOR="tu_correo@gmail.com"
export CONTRASENA_CORREO="tu_contrasena_de_aplicacion"
export CORREO_RECEPTOR="destinatario@gmail.com"
```

---

## Uso

Una vez configuradas las credenciales, ejecuta el script con el siguiente comando:

```bash
python pokemon_script.py
```

Al finalizar, se generara el archivo `pokemon_del_dia.xlsx` en el directorio raiz del proyecto y se enviara automaticamente por correo al destinatario configurado.

---

## Estructura del proyecto

```
pokemon-del-dia/
|-- pokemon_script.py       # Script principal
|-- .env                    # Variables de entorno con credenciales (no se sube a Git)
|-- .env.example            # Plantilla de variables de entorno sin valores reales
|-- .gitignore              # Archivos y carpetas excluidos del repositorio
|-- README.md               # Documentacion del proyecto
```

---

## Notas de seguridad

- El archivo `.env` esta incluido en `.gitignore` y nunca debe subirse al repositorio.
- No escribas tus credenciales directamente en el codigo fuente.
- Utiliza siempre contrasenas de aplicacion en lugar de la contrasena principal de tu cuenta de Gmail.
- El archivo `pokemon_del_dia.xlsx` tambien esta excluido del repositorio al ser un archivo generado automaticamente en cada ejecucion.
