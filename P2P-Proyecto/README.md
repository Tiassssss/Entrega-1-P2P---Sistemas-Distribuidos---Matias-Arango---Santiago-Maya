# Sistema P2P de Compartición de Archivos

## 📋 Descripción General

Este sistema **Peer-to-Peer (P2P)** permite compartir archivos entre varios nodos (peers) de manera distribuida y descentralizada, usando Python. La arquitectura combina un servidor de directorio central (Maestro) y comunicación directa entre peers usando **API REST** y **gRPC**.

## 🏗️ Arquitectura del Sistema

### Componentes

- **Maestro** (`maestro/`):
  - Servidor central que registra los peers y los archivos disponibles en la red.
  - Permite localizar qué peer tiene cada archivo.

- **Peers** (`peer1/`, `peer2/`, `peer3/`):
  - Cada peer tiene microservicios REST y gRPC.
  - REST: consultas, registro, descubrimiento y listado de archivos.
  - gRPC: transferencia de archivos (upload/download dummy).
  - Cliente P2P para interactuar con otros peers y el Maestro.

- **Protocolos**:
  - **REST API**: Para consultas y descubrimiento de archivos.
  - **gRPC**: Para transferencia binaria de archivos.
  - **Protocol Buffers** (`proto/`): Definición de servicios gRPC.

## 🚀 Funcionalidades Implementadas

- Registro automático de peers en el Maestro al iniciar.
- Listado y consulta de archivos disponibles en cada peer.
- Descubrimiento de archivos vía Maestro (centralizado) y entre peers amigos (descentralizado).
- Transferencia de archivos entre peers usando gRPC (servicios dummy).
- Configuración dinámica de cada peer mediante archivo `config.json`.
- Concurrencia en los servidores gRPC usando ThreadPoolExecutor.
- Red de peers amigos (primario y suplente) para consultas distribuidas.

## 📁 Estructura del Proyecto

```
p2p_project/
├── maestro/
│   ├── server_maestro.py
│   └── config.json
├── peer1/
│   ├── server_rest.py
│   ├── server_grpc.py
│   ├── client.py
│   ├── run_peer.py
│   ├── config.json
│   └── peer1/shared/
├── peer2/ (igual estructura)
├── peer3/ (igual estructura)
├── proto/
│   └── files.proto
├── common/
│   ├── files_pb2.py
│   ├── files_pb2_grpc.py
│   └── grpc_client.py
├── prueba_completa.sh
├── start_component.sh
└── README.md
```

## ⚙️ Configuración del Sistema

Cada peer tiene un archivo `config.json` con:

```json
{
  "id": "P1",
  "ip": "0.0.0.0",
  "port": 8000,
  "grpc_port": 50051,
  "shared_dir": "peer1/shared",
  "maestro_url": "http://localhost:9000",
  "friend_peer_primary": "http://localhost:8001",
  "friend_peer_backup": "http://localhost:8002"
}
```

## 🔄 Flujo de Operaciones

1. **Bootstrap**: Cada peer lee su configuración, escanea su directorio de archivos y se registra en el Maestro.
2. **Descubrimiento**:
   - Vía Maestro: consulta centralizada de qué peer tiene un archivo.
   - Vía peer amigo: consulta distribuida entre peers configurados como amigos.
3. **Transferencia**:
   - Descarga y subida de archivos entre peers usando gRPC (servicios dummy, no transferencia real).

## 🧪 Ejecución y Pruebas

- **Prueba completa automatizada**:
  ```bash
  ./prueba_completa.sh
  ```
  Inicia todos los componentes, realiza registros, pruebas de descubrimiento y transferencia.

- **Inicio manual**:
  ```bash
  ./start_component.sh maestro
  ./start_component.sh peer1
  ./start_component.sh peer2
  ./start_component.sh peer3
  ```

- **Verificación manual**:
  - Estado del Maestro: `curl http://localhost:9000/`
  - Peers registrados: `curl http://localhost:9000/peers`
  - Archivos de un peer: `curl http://localhost:8000/files`
  - Buscar archivo: `curl "http://localhost:9000/locate?file=archivo1.txt"`

## 🛠️ Tecnologías Utilizadas

- Python 3.8+
- FastAPI (REST)
- gRPC
- Protocol Buffers
- Uvicorn
- ThreadPoolExecutor
- Requests

## 📊 Características Clave

- Microservicios REST y gRPC separados por peer
- Concurrencia en servidores gRPC
- Descubrimiento dual (centralizado y P2P)
- Configuración flexible por archivo JSON
- Red de peers amigos para consultas distribuidas
- Registro automático y listado de archivos
- Transferencia dummy de archivos entre peers

---

**Este README describe únicamente las funcionalidades realmente implementadas en el sistema actual.**