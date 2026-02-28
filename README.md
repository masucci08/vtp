# vtp
# Ejecucion de vtp attack con Scapy

**Estudiante:** Masucci Franco Rincón  
**Matrícula:** 2024-1250  
**Asignatura:** Seguridad de Redes  
**Fecha:** 27/02/2026  


---

### Descripción y Topología 

El laboratorio se ha desplegado en un entorno virtualizado utilizando **GNS3**, simulando una infraestructura de red corporativa vulnerada desde el interior.

### Detalles de la Topología

* **Direccionamiento IP:** Subred `10.12.50.0/24`.
<img width="459" height="285" alt="image" src="https://github.com/user-attachments/assets/f8f18212-26ac-4ce2-b1fb-482d6a8a3592" />


| Dispositivo | Interfaz | Dirección IP | Máscara de Subred | Gateway Predeterminado |
| :--- | :--- | :--- | :--- | :--- |
| **R1** | e0/0 | 10.12.50.1 | 255.255.255.0 (/24) |    |
| **gnsattack (atacante)** | eth0 | 10.12.50.13 | 255.255.255.0 (/24) | 10.12.50.1 |
| **VPCS (víctima)** | e0/0 | 10.12.50.11  | 255.255.255.0 (/24) | 10.12.501 |


### Objetivo del Script
El objetivo del script es demostrar la vulnerabilidad del protocolo VTP (VLAN Trunking Protocol) cuando no está correctamente asegurado, permitiendo a un atacante introducir cambios maliciosos en la base de datos de VLAN del dominio VTP.


### Parámetros Usados
* **Interfaz:** `eth0`
* **Dirección Destino:** Multicast Cisco `01:00:0c:cc:cc:cc`.
* **Campos Falsificados (TLVs):**
    * *Device ID:* Generado aleatoriamente (`R1`).
    * *Port ID:* Simulación de interfaces Ethernet (`Ethernet0/x`).
    * *Capabilities:* Flag `0x0001` (Simulación de rol de Router).

## Evidencia de Ejecución
## 1-
<img width="443" height="231" alt="image" src="https://github.com/user-attachments/assets/ed1a9521-bc04-44c5-85e8-211489fdcb39" />





---

### Requisitos para utilizar la herramienta.
Tener python3 instalado en la maquina atacante


### Medidas de Mitigación
Para proteger la infraestructura contra estos vectores de ataque, se recomiendan las siguientes configuraciones de endurecimiento (Hardening):
Agrega VLANs falsas

Borra VLANs legítimas

Cambia la base de datos del dominio VTP

Propaga cambios a todos los switches
