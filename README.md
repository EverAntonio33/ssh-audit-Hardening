# Auditoría y Hardening de SSH en Kali Linux

Este repositorio documenta el proceso práctico de auditoría de seguridad y endurecimiento (*hardening*) del servicio SSH en un entorno de pruebas con **Kali Linux** (ejecutado sobre VirtualBox), con el objetivo de eliminar vulnerabilidades por algoritmos obsoletos y cumplir con estándares recomendados de ciberseguridad.

---

## 🛠️ 1. Herramientas y Entorno Utilizados
* **Sistema Operativo:** Kali Linux (VirtualBox)
* **Servicio Evaluado:** OpenSSH Server (`sshd`)
* **Herramienta de Auditoría:** `ssh-audit`

---

## 🔍 2. Estado Inicial (Antes del Hardening)
Al realizar la primera auditoría del servicio SSH por defecto, se identificaron vulnerabilidades críticas y advertencias de seguridad relacionadas con algoritmos criptográficos débiles u obsoletos:
* **Uso del hash SHA-1 (`hmac-sha1`):** Marcado en rojo (`[fail]`) por considerarse criptográficamente débil y vulnerable a ataques de colisión.
* **Algoritmos y etiquetas de 64 bits (`umac-64`):** Advertencias en amarillo (`[warn]`) por su bajo nivel de seguridad frente a ataques modernos.

> **Evidencia (Antes):**
<img width="1084" height="620" alt="Captura de pantalla 2026-10-09 213935" src="https://github.com/user-attachments/assets/5e8bb9a3-61ef-4ba8-888b-7d235ced2d3d" />


---

## ⚙️ 3. Proceso de Mitigación y Hardening
Para corregir los hallazgos anteriores, se modificó el archivo de configuración principal del servicio SSH:

1. Se abrió el archivo de configuración con privilegios de superusuario:
   ```bash
   sudo nano /etc/ssh/sshd_config


## 4. Estado Final (Después del Hardening)
> **Evidencia (Después):**
> <img width="1336" height="788" alt="Captura de pantalla 2026-10-09 215146" src="https://github.com/user-attachments/assets/2ee806ae-5806-43f5-a327-2218a48aa761" />
