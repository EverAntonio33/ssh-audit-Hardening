# Auditoría y Hardening de SSH en Kali Linux

Este repositorio documenta el proceso práctico de auditoría de seguridad y endurecimiento (*hardening*) del servicio SSH en un entorno de pruebas con **Kali Linux** (ejecutado sobre VirtualBox), con el objetivo de eliminar vulnerabilidades por algoritmos obsoletos y cumplir con estándares recomendados de ciberseguridad.

---

## 🛠️ 1. Herramientas y Entorno Utilizados
* **Sistema Operativo:** Kali Linux[cite: 1] (VirtualBox)
* **Servicio Evaluado:** OpenSSH Server (`sshd`)
* **Herramienta de Auditoría:** `ssh-audit`

---

## 🔍 2. Estado Inicial (Antes del Hardening)
Al realizar la primera auditoría del servicio SSH por defecto, se identificaron vulnerabilidades críticas y advertencias de seguridad relacionadas con algoritmos criptográficos débiles u obsoletos:
* **Uso del hash SHA-1 (`hmac-sha1`):** Marcado en rojo (`[fail]`) por considerarse criptográficamente débil y vulnerable a ataques de colisión.
* **Algoritmos y etiquetas de 64 bits (`umac-64`):** Advertencias en amarillo (`[warn]`) por su bajo nivel de seguridad frente a ataques modernos.

> **Evidencia (Antes):**
> *[Inserta aquí tu primera captura de pantalla con los errores en rojo]*

---

## ⚙️ 3. Proceso de Mitigación y Hardening
Para corregir los hallazgos anteriores, se modificó el archivo de configuración principal del servicio SSH:

1. Se abrió el archivo de configuración con privilegios de superusuario:
   ```bash
   sudo nano /etc/ssh/sshd_config
