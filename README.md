# 🌐 Sistema P2P de Compartición de Archivos# 🌐 Sistema P2P de Compartición de Archivos 

# Realizador Por Santiago Maya Horta y Matias Arango Ruiz



Un sistema **Peer-to-Peer (P2P)** distribuido que permite la compartición descentralizada de archivos entre múltiples nodos de red. El proyecto implementa una arquitectura híbrida que combina un servidor maestro para el descubrimiento de peers con transferencias directas entre nodos.Un sistema **Peer-to-Peer (P2P)** distribuido para compartición de archivos implementado en Python, utilizando **REST API** y **gRPC** para comunicación entre peers.



## 🎯 ¿Qué hace este proyecto?## 🚀 Inicio Rápido



Este sistema P2P permite que múltiples computadoras (peers) compartan archivos de manera eficiente:### 1. Activar Entorno

```bash

- **📁 Compartición distribuida**: Cada peer puede compartir sus archivos con la redcd P2P-Proyecto

- **🔍 Descubrimiento automático**: Los peers se registran automáticamente y pueden encontrar archivos en otros nodossource venv/bin/activate

- **⚡ Transferencias directas**: Los archivos se transfieren directamente entre peers usando gRPC```

- **🌐 Red de amigos**: Los peers mantienen conexiones con otros nodos conocidos

- **📊 Directorio centralizado**: Un servidor maestro mantiene un índice global de archivos disponibles### 2. Ejecutar Sistema Completo

```bash

## 🏗️ Arquitectura del Sistemabash prueba_completa.sh

```

### Componentes Principales

### 3. Verificar Estado

#### 🎯 **Servidor Maestro** (Puerto 9000)```bash

- **Propósito**: Servidor de directorio centralizado que coordina la red P2Pcurl http://localhost:9000/peers

- **Funciones**:```

  - Registro y gestión de peers activos

  - Índice global de archivos disponibles en la red## � Componentes

  - Servicio de localización de archivos

  - API REST para consultas del directorio- **🎯 Maestro** (puerto 9000): Servidor de directorio central

- **🔵 Peer 1** (REST: 9001, gRPC: 9002): Nodo P2P

#### 🔵🟢🟡 **Peers** (Nodos P2P)- **🟢 Peer 2** (REST: 9003, gRPC: 9004): Nodo P2P  

Cada peer opera con dos servidores:- **🟡 Peer 3** (REST: 9005, gRPC: 9006): Nodo P2P



**REST API Server** (Puertos 9001, 9003, 9005):## 🧪 Pruebas Rápidas

- Gestión del estado del peer

- Consulta de archivos locales```bash

- Comunicación con el maestro# Ver directorio completo

- Red de peers amigoscurl http://localhost:9000/directory



**gRPC Server** (Puertos 9002, 9004, 9006):# Buscar archivo

- Transferencias directas de archivoscurl "http://localhost:9000/locate?file=archivo1.txt"

- Comunicación peer-to-peer eficiente

- Protocolo binario optimizado# Transferir archivo (desde peer1/)

python client.py --action download --file archivo3.txt

### Estructura de Directorios```



```## 📖 Documentación Completa

P2P-Proyecto/

├── 📄 README.md                    # Este archivo (descripción del proyecto)Para instrucciones detalladas, consulta: **[README_GUIA_EJECUCION.md](README_GUIA_EJECUCION.md)**

├── 📋 README_GUIA_EJECUCION.md     # Guía completa de instalación y uso

├── 🔍 verificar_sistema.sh         # Script de verificación del sistema## ⚡ Funcionalidades

├── 🚀 prueba_completa.sh          # Script de ejecución automática

├── - ✅ Registro automático de peers

├── 🎯 maestro/                     # Servidor maestro (directorio centralizado)- ✅ Descubrimiento centralizado y P2P

│   ├── server_maestro.py          # Lógica del servidor de directorio- ✅ Transferencias gRPC bidireccionales

│   └── config.json                # Configuración del maestro- ✅ Actualización automática del maestro

├── - ✅ Red de peers amigos

├── 🔵 peer1/                       # Primer nodo P2P- ✅ API REST completa

│   ├── run_peer.py                # Lanzador del peer

│   ├── server_rest.py             # API REST del peer## 🛠️ Tecnologías

│   ├── server_grpc.py             # Servidor gRPC para transferencias

│   ├── client.py                  # Cliente para transferencias- **Python 3.8+**

│   ├── config.json                # Configuración del peer- **FastAPI** (REST)

│   └── shared/                    # Archivos compartidos del peer- **gRPC** (Transferencias)

│       └── archivo1.txt- **Protocol Buffers**

├── - **Uvicorn** (ASGI Server)

├── 🟢 peer2/                       # Segundo nodo P2P

│   ├── [misma estructura que peer1]---

│   └── shared/

│       └── archivo2.txt� **Para guía completa de instalación, configuración y uso**: [README_GUIA_EJECUCION.md](README_GUIA_EJECUCION.md)
├── 
├── 🟡 peer3/                       # Tercer nodo P2P
│   ├── [misma estructura que peer1]
│   └── shared/
│       └── archivo3.txt
├── 
├── 🔌 common/                      # Código compartido
│   ├── grpc_client.py             # Cliente gRPC reutilizable
│   ├── files_pb2.py               # Clases generadas de Protocol Buffers
│   └── files_pb2_grpc.py          # Servicios gRPC generados
└── 
└── 📝 proto/                       # Definiciones de Protocol Buffers
    └── files.proto                # Esquema de mensajes gRPC
```

## ⚡ Características Principales

### 🌟 **Funcionalidades Core**
- **Registro automático de peers** en el servidor maestro
- **Descubrimiento centralizado** de archivos a través del maestro
- **Transferencias P2P directas** usando gRPC para eficiencia
- **Sincronización automática** del directorio tras transferencias
- **Red de peers amigos** para descubrimiento distribuido

### 🔧 **Tecnologías Utilizadas**
- **🐍 Python 3.8+**: Lenguaje base del sistema
- **⚡ FastAPI**: Framework web para APIs REST rápidas y modernas
- **🚀 gRPC**: Protocolo de comunicación de alto rendimiento
- **📡 Protocol Buffers**: Serialización eficiente de datos
- **🌐 Uvicorn**: Servidor ASGI para aplicaciones asíncronas
- **📨 Requests**: Cliente HTTP para comunicación entre servicios

### 🔄 **Flujo de Operación**
1. **Inicio**: Los peers se registran automáticamente en el maestro
2. **Descubrimiento**: Los usuarios consultan qué archivos están disponibles
3. **Localización**: El maestro indica qué peer tiene cada archivo
4. **Transferencia**: Los peers se conectan directamente para transferir archivos
5. **Actualización**: El directorio se actualiza automáticamente tras cada transferencia

## 📖 Documentación

- **📋 [README_GUIA_EJECUCION.md](README_GUIA_EJECUCION.md)**: Guía completa de instalación, configuración y uso
- **🔍 [verificar_sistema.sh](verificar_sistema.sh)**: Script para verificar el estado del sistema
- **🚀 [prueba_completa.sh](prueba_completa.sh)**: Ejecución automática de todo el sistema

---

💡 **Para ejecutar el proyecto**: Consulta la [Guía de Ejecución](README_GUIA_EJECUCION.md)
