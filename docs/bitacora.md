# Bitácora del laboratorio

Este documento registra los avances, evidencias y decisiones del laboratorio.

## 28 de agosto de 2026 - Preparación de Windows Server

### Objetivo

Preparar la primera máquina virtual que se utilizará como servidor del laboratorio.

### Evidencia observada

- Hipervisor: Oracle VirtualBox.
- Sistema operativo invitado: Windows Server 2022 de 64 bits.
- Máquina virtual iniciada correctamente.
- Memoria asignada actualmente: 2048 MB.
- Se configuró la cuenta local `Administrador` sin registrar sus credenciales.
- Se inició sesión correctamente.
- El Administrador del servidor se abrió y el sistema quedó listo para su configuración inicial.
- La máquina virtual funciona en modo de ventana normal.

### Estado

✅ Instalación de Windows Server 2022 completada.

### Incidencia resuelta

**Problema:** La combinación `Ctrl + Alt + Supr` se ejecutaba en el equipo anfitrión y no en la máquina virtual.

**Diagnóstico:** Windows reserva esa combinación para el sistema anfitrión.

**Solución:** Se utilizó la tecla anfitrión de VirtualBox (`Ctrl derecho`) para enviar la combinación al sistema invitado.

**Resultado:** Se pudo iniciar sesión en Windows Server correctamente.

### Decisión de recursos

El equipo anfitrión dispone de 32 GB de RAM. Se decidió mantener temporalmente 2048 MB en la máquina virtual para comprobar su funcionamiento. Si el Administrador del servidor o los futuros roles responden con lentitud, se aumentará la memoria a 4096 o 6144 MB.

### Observaciones

- Las credenciales no se registran en el repositorio.
- El consumo de memoria y la fluidez se revisarán durante la instalación de los roles.

## 28 de agosto de 2026 - Revisión de configuración inicial

### Configuración observada

- Nombre automático del equipo: `WIN-NIB11NB3RP4`.
- Pertenencia actual: grupo de trabajo `WORKGROUP`.
- Red Ethernet: dirección IPv4 asignada mediante DHCP; IPv6 habilitado.
- Firewall de Microsoft Defender: activado para el perfil privado.
- Escritorio remoto: deshabilitado.
- Sistema: Windows Server 2022 Standard Evaluation.
- Memoria de la máquina virtual: 2 GB.
- Disco virtual disponible: aproximadamente 49 GB.

## 28 de agosto de 2026 - Cambio de nombre

### Acción realizada

El nombre automático del servidor se sustituyó por `DC01-AMINE`, elegido para identificar el primer controlador de dominio del laboratorio.

### Resultado

✅ El nuevo nombre aparece en el Administrador del servidor después del reinicio.

## 28 de agosto de 2026 - Diseño inicial de red

### Configuración observada

- Adaptador actual conectado mediante NAT de VirtualBox.
- Dirección IPv4 recibida por DHCP: `10.0.2.15`.
- Máscara de subred: `255.255.255.0` (`/24`).
- Puerta de enlace NAT: `10.0.2.2`.

### Decisión de diseño

El adaptador NAT se conservará para proporcionar acceso a Internet. Se añadirá un segundo adaptador conectado a una red interna llamada `LAB-AD`. Ese adaptador se utilizará para la comunicación entre el controlador de dominio y los futuros clientes, y recibirá una dirección IP estática.

### Próxima acción

Añadir el segundo adaptador de red interna en VirtualBox.
