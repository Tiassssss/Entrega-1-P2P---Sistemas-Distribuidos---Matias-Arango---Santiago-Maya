# 🌐 Sistema P2P de Compartición de Archivos

## Realizado Por
**Santiago Maya Horta (ID:000190981) y Matias Arango Ruiz (ID:000547025)**

---

## 📝 Descripción

Un sistema **Peer-to-Peer (P2P)** distribuido que permite la compartición descentralizada de archivos entre múltiples nodos de red. El proyecto implementa una arquitectura híbrida que combina un servidor maestro para el descubrimiento de peers con transferencias directas entre nodos.  
Sistema implementado en **Python**, utilizando **REST API** y **gRPC** para comunicación entre peers.

---

## 🎯 ¿Qué hace este proyecto?

Este sistema P2P permite que múltiples computadoras (peers) compartan archivos de manera eficiente:

- **📁 Compartición distribuida**: Cada peer puede compartir sus archivos con la red.
- **🔍 Descubrimiento automático**: Los peers se registran automáticamente y pueden encontrar archivos en otros nodos.
- **⚡ Transferencias directas**: Los archivos se transfieren directamente entre peers usando gRPC.
- **🌐 Red de amigos**: Los peers mantienen conexiones con otros nodos conocidos.
- **📊 Directorio centralizado**: Un servidor maestro mantiene un índice global de archivos disponibles.

---

## 🏗️ Arquitectura del Sistema

### Componentes Principales

#### 🎯 Servidor Maestro (Puerto 9000)
- **Propósito**: Servidor de directorio centralizado que coordina la red P2P.
- **Funciones**:
  - Registro y gestión de peers activos.
  - Índice global de archivos disponibles en la red.
  - Servicio de localización de archivos.
  - API REST para consultas del directorio.

#### 🔵🟢🟡 Peers (Nodos P2P)
Cada peer opera con dos servidores:

- **REST API Server** (Puertos 9001, 9003, 9005):
  - Gestión del estado del peer.
  - Consulta de archivos locales.
  - Comunicación con el maestro.
  - Red de peers amigos.

- **gRPC Server** (Puertos 9002, 9004, 9006):
  - Transferencias directas de archivos.
  - Comunicación peer-to-peer eficiente.
  - Protocolo binario optimizado.

---

## 🚀 Componentes

- **🎯 Maestro** (puerto 9000): Servidor de directorio central.
- **🔵 Peer 1** (REST: 9001, gRPC: 9002): Nodo P2P.
- **🟢 Peer 2** (REST: 9003, gRPC: 9004): Nodo P2P.
- **🟡 Peer 3** (REST: 9005, gRPC: 9006): Nodo P2P.

---

## 🧪 Pruebas Rápidas

### 1. Activar Entorno
```bash
cd P2P-Proyecto
source venv/bin/activate
```

### 2. Ejecutar Sistema Completo
```bash
bash prueba_completa.sh
```

### 3. Verificar Estado
```bash
curl http://localhost:9000/peers
```

### Ejemplos de comandos

- Ver directorio completo:
    ```bash
    curl http://localhost:9000/directory
    ```

- Buscar archivo:
    ```bash
    curl "http://localhost:9000/locate?file=archivo1.txt"
    ```

- Transferir archivo (desde peer1/):
    ```bash
    python client.py --action download --file archivo3.txt
    ```

---

## 🗂️ Estructura de Directorios

```
P2P-Proyecto/
├── README.md                    # Este archivo (descripción del proyecto)
├── README_GUIA_EJECUCION.md     # Guía completa de instalación y uso
├── verificar_sistema.sh         # Script de verificación del sistema
├── prueba_completa.sh           # Script de ejecución automática
├── maestro/                     # Servidor maestro (directorio centralizado)
│   ├── server_maestro.py        # Lógica del servidor de directorio
│   └── config.json              # Configuración del maestro
├── peer1/                       # Primer nodo P2P
│   ├── run_peer.py              # Lanzador del peer
│   ├── server_rest.py           # API REST del peer
│   ├── server_grpc.py           # Servidor gRPC para transferencias
│   ├── client.py                # Cliente para transferencias
│   ├── config.json              # Configuración del peer
│   └── shared/                  # Archivos compartidos del peer
│       └── archivo1.txt
├── peer2/                       # Segundo nodo P2P
│   ├── [misma estructura que peer1]
│   └── shared/
│       └── archivo2.txt
├── peer3/                       # Tercer nodo P2P
│   ├── [misma estructura que peer1]
│   └── shared/
│       └── archivo3.txt
├── common/                      # Código compartido
│   ├── grpc_client.py           # Cliente gRPC reutilizable
│   ├── files_pb2.py             # Clases generadas de Protocol Buffers
│   └── files_pb2_grpc.py        # Servicios gRPC generados
└── proto/                       # Definiciones de Protocol Buffers
    └── files.proto              # Esquema de mensajes gRPC
```

---

## ⚡ Características Principales

### 🌟 Funcionalidades Core
- **Registro automático de peers** en el servidor maestro.
- **Descubrimiento centralizado** de archivos a través del maestro.
- **Transferencias P2P directas** usando gRPC para eficiencia.
- **Sincronización automática** del directorio tras transferencias.
- **Red de peers amigos** para descubrimiento distribuido.

---

## 🔧 Tecnologías Utilizadas

- **🐍 Python 3.8+**: Lenguaje base del sistema.
- **⚡ FastAPI**: Framework web para APIs REST rápidas y modernas.
- **🚀 gRPC**: Protocolo de comunicación de alto rendimiento.
- **📡 Protocol Buffers**: Serialización eficiente de datos.
- **🌐 Uvicorn**: Servidor ASGI para aplicaciones asíncronas.
- **📨 Requests**: Cliente HTTP para comunicación entre servicios.

---

## 🔄 Flujo de Operación

1. **Inicio**: Los peers se registran automáticamente en el maestro.
2. **Descubrimiento**: Los usuarios consultan qué archivos están disponibles.
3. **Localización**: El maestro indica qué peer tiene cada archivo.
4. **Transferencia**: Los peers se conectan directamente para transferir archivos.
5. **Actualización**: El directorio se actualiza automáticamente tras cada transferencia.

---

## 📖 Documentación

- **📋 [README_GUIA_EJECUCION.md](P2P-Proyecto/README_GUIA_EJECUCION.md)**: Guía completa de instalación, configuración y uso.
- **🔍 [verificar_sistema.sh](P2P-Proyecto/verificar_sistema.sh)**: Script para verificar el estado del sistema.
- **🚀 [prueba_completa.sh](P2P-Proyecto/prueba_completa.sh)**: Ejecución automática de todo el sistema.



