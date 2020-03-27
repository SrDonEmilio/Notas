# Infrared [OpenStack Lab]

Meetup Fedora México - Reunión de Marzo

## ¿Qué es Open Stack?

Servicio DevOps para la automatización de procesos en servidor, es un enviroment bastante compejo, pero muy potente.

### Tipos de Nodos

- Controller : DB y APIs
- Compute: Hypervisor
- Storage (No es muy general)

## ¿Cómo funciona el Lab?

Hay dos formas de hacerlo 

- All in one: Pruebas de servicios juntos

- Multi-nodes: Pruebas con servicios separados

Usando varios diseños de arquitecturas, podemos distribuir y organizar los procesos y configuraciones

## ¿Qué es Infrared?

Es un sistema de plugins basados en Ansible para automatizar creación, configuración y montaje de Máquinas Virtuales desde una Máquina Física como director.

### Requisitos

- Servidor físico con al menos
  - 48 GB RAM
  - 150 GB HDD (Puedes tener uno de 70 GB con comprensión btrfs y zlib)
- Fedora 25, CentOS o RHEL 7

Infrared está desarrollado para usarse con Python 2.7, todavía no está listo con el 7 (26/03/2020) .

### Herramientas recomendadas

- screen y/o tlog (guardar sesiones)
- time (medir tiempo de operación de comandos)
- Destruir VM's y restaurar configuración inicial







