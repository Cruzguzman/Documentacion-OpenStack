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