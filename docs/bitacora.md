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

### Observaciones

- Las credenciales no se registran en el repositorio.
- Antes de instalar roles se revisarán los recursos asignados a la máquina virtual. Si el equipo anfitrión lo permite, se valorará aumentar la memoria a 4096 MB para trabajar con mayor fluidez.
