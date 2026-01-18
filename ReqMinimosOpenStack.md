# Checklist de instalación local de OpenStack

## 1. Hardware mínimo
- ✅ 16 GB de RAM (recomendado: 32 GB+ para múltiples nodos)
- ✅ 4 núcleos de CPU con soporte de virtualización (Intel VT-x / AMD-V)
- ✅ 100 GB de espacio en disco (SSD recomendado)
- ✅ Al menos 2 interfaces de red físicas o virtuales

## 2. Sistema Operativo
- ✅ Ubuntu Server 20.04 LTS (recomendado por soporte y documentación)
- ✅ Acceso root o permisos sudo
- ✅ Actualizaciones aplicadas (`apt update && apt upgrade`)

## 3. Red
- ✅ Configuración de una interfaz para administración
- ✅ Configuración de otra interfaz para tráfico interno de OpenStack
- ✅ Conexión a Internet estable para descargar paquetes

## 4. Software y dependencias
- ✅ Python 3.x instalado
- ✅ Paquetes básicos: `git`, `curl`, `wget`, `net-tools`, `openssh-server`
- ✅ Virtualización habilitada en BIOS/UEFI

## 5. Opciones de despliegue
- 🔹 **DevStack**: instalación rápida para pruebas y desarrollo (todo en un solo nodo).
- 🔹 **Packstack**: instalación simplificada en distribuciones basadas en RHEL/CentOS.
- 🔹 **Manual/Multi-nodo**: instalación completa para simular entornos de producción.

## 6. Consideraciones adicionales
- ⚠️ OpenStack es intensivo en recursos: planifica según tu hardware.
- ⚠️ Mantén imágenes y paquetes actualizados.
- ⚠️ Configura firewalls y aislamiento de red desde el inicio.
- ⚠️ Usa snapshots o backups antes de cambios grandes.

---

### 📌 Tip
Si tu hardware es limitado, comienza con **DevStack en modo all-in-one** para familiarizarte con los servicios principales (Nova, Neutron, Cinder, Keystone, Glance, Horizon).

# Opciones de ambientación de OpenStack en Windows

## 1. Windows + Máquina Virtual (VM con Linux)
- **Cómo:** Instalar VirtualBox, VMware o Hyper-V y correr Ubuntu/CentOS dentro.
- ✅ Pros:
  - Entorno aislado y controlado.
  - Compatible con la documentación oficial de OpenStack.
  - Fácil de resetear con snapshots.
- ❌ Contras:
  - Consumo alto de recursos (RAM/CPU).
  - Rendimiento limitado por la capa de virtualización.
  - Configuración de red más compleja.

## 2. Windows + WSL2 (Windows Subsystem for Linux)
- **Cómo:** Usar WSL2 con Ubuntu y desplegar OpenStack/DevStack dentro.
- ✅ Pros:
  - Integración directa con Windows.
  - Menor consumo de recursos que una VM completa.
  - Ideal para pruebas rápidas y desarrollo.
- ❌ Contras:
  - Networking limitado (no soporta todas las funciones de Neutron).
  - No apto para escenarios multi-nodo.
  - Menor soporte oficial comparado con Linux nativo.

## 3. Linux Nativo (Servidor dedicado o dual boot)
- **Cómo:** Instalar Ubuntu Server directamente en hardware o en dual boot.
- ✅ Pros:
  - Máxima compatibilidad y rendimiento.
  - Soporte completo de todos los servicios OpenStack.
  - Escalable hacia entornos productivos.
- ❌ Contras:
  - Requiere dedicar hardware o partición.
  - Menos conveniente si tu entorno principal es Windows.
  - Migración de datos entre Windows/Linux puede ser un reto.

---

## 📌 Conclusión
- **Laboratorio rápido:** WSL2 es suficiente para aprender conceptos básicos.  
- **Pruebas más completas:** VM con Linux es viable, aunque con penalización de rendimiento.  
- **Escenarios serios o productivos:** Linux nativo es la única opción sostenible a largo plazo.

# Guía paso a paso para instalar Ubuntu

## 1. Preparativos
- ✅ Descarga la ISO oficial desde [ubuntu.com/download](https://ubuntu.com/download).
- ✅ Elige la versión **Ubuntu Desktop 22.04 LTS** o **Ubuntu Server 22.04 LTS** según tu necesidad.
- ✅ Crea un medio de instalación:
  - USB booteable con **Rufus** (Windows) o **balenaEtcher** (multiplataforma).
  - O monta la ISO directamente si usarás una máquina virtual (VirtualBox, VMware, Hyper-V).

## 2. Configuración del arranque
- ✅ Inserta el USB en tu PC o carga la ISO en la VM.
- ✅ Reinicia y entra al BIOS/UEFI (tecla común: F2, F12, DEL, ESC).
- ✅ Configura el **orden de arranque** para que inicie desde el USB/ISO.

## 3. Inicio del instalador
- ✅ Selecciona **Try Ubuntu** (para probar sin instalar) o **Install Ubuntu**.
- ✅ Elige idioma y distribución de teclado.
- ✅ Conéctate a Internet (opcional, pero recomendado para actualizaciones durante la instalación).

## 4. Opciones de instalación
- ✅ Selecciona tipo de instalación:
  - **Normal Installation:** incluye navegador, utilidades, software básico.
  - **Minimal Installation:** solo lo esencial (más ligero).
- ✅ Marca la opción de instalar actualizaciones y drivers de terceros si lo deseas.

## 5. Particionado del disco
- ✅ Elige:
  - **Erase disk and install Ubuntu:** instalación limpia (borra todo).
  - **Manual partitioning:** si quieres personalizar particiones (ej. `/`, `/home`, `swap`).
- ✅ Recomendación básica:
  - `/` (root): 30 GB+
  - `/home`: resto del espacio
  - `swap`: 2–4 GB (si tienes poca RAM)

## 6. Configuración de usuario
- ✅ Define tu nombre, nombre de equipo y usuario.
- ✅ Crea una contraseña segura.
- ✅ Decide si quieres iniciar sesión automáticamente o pedir contraseña.

## 7. Instalación
- ✅ El instalador copiará archivos y configurará el sistema.
- ✅ Al terminar, reinicia y retira el USB/ISO.

## 8. Post-instalación
- ✅ Actualiza paquetes:
  ```bash 
  sudo apt update && sudo apt upgrade -y
  