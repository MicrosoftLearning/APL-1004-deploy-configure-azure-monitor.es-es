---
lab:
  title: 'Ejercicio: Configuración de la supervisión de los servicios de proceso'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tareas de aptitudes

- Creación de un punto de conexión de recopilación de datos
- Creación de una regla de recopilación de datos
- Agregar una colección de registros de IIS a una regla de recopilación de datos existente
- Configuración de Network Connection Monitor para una máquina virtual IaaS de Linux

## Instrucciones del ejercicio

### Creación de un punto de conexión de recopilación de datos

1. En la barra de búsqueda de Azure Portal, escribe **Monitor** y selecciona **Monitor** en la lista de resultados.
1. En la página **Monitor**, en la sección **Configuración**, elige **Puntos de conexión de recopilación de datos**.
1. En la página **Puntos de conexión de recopilación de datos**, selecciona **Crear**.
1. En la página Crear punto de conexión de recopilación de datos, proporciona los siguientes valores y elige Revisar y crear.

    | Propiedad | Valor    |
    |:---------|:---------|
    | El nombre del punto de conexión  | IaaSVMCollectionEndpoint   |
    | Subscription  | Su suscripción  |
    | Grupo de recursos    | rg-alpha  |
    | Region    | Este de EE. UU.  |

5. Revisa los valores y selecciona **Crear**.

### Creación de una regla de recopilación de datos

1. En la barra de búsqueda de Azure Portal, escribe **Monitor** y selecciona **Monitor** en la lista de resultados.
1. En la página **Monitor**, en la sección **Configuración**, elige **Reglas de recopilación de datos**.
1. En la página **Reglas de recopilación de datos**, elige **Crear**.
1. En la página **Crear regla de recopilación de datos**, configura las opciones siguientes y elige **Siguiente**.

    | Propiedad | Valor    |
    |:---------|:---------|
    | Nombre de la regla  | WinVMDCR   |
    | Subscription  | Su suscripción   |
    | Grupo de recursos    | rg-alpha  |
    | Region    | Este de EE. UU.  |
    | Tipo de plataforma | Windows  |
    | Punto de conexión de recopilación de datos  | IaaSVMCollectionEndpoint   |

5. En la página **Recursos**, haz clic en **Agregar recursos**.
1. En la página **Seleccionar un ámbito**, activa la casilla **WS-VM1** y elige **Aplicar**.
1. En la página **Crear regla de recopilación de datos**, elige **Siguiente**.
1. En la pestaña **Recopilar y entregar**, elige **Agregar origen de datos**.
1. En la página **Agregar origen de datos**, selecciona **Registros de eventos de Windows**. En la categoría **Aplicación**, activa las categorías **Crítico** y **Error**. En la categoría **Seguridad**, elige la categoría **Error de auditoría**. En la categoría **Sistema**, activa las categorías **Crítico** y **Error**. 
1. Elija **Siguiente**.
1. En la página **Destino**, configura estos valores:

    | Propiedad | Valor    |
    |:---------|:---------|
    | Tipo de destino  | Registros de Azure Monitor   |
    | Subscription  | Su suscripción   |
    | Cuenta o espacio de nombres  | LogAnalytics1  |

12. Elige **Agregar origen de datos**.
1. Elige **Revisar y crear** y luego elige **Crear**.


### Agregar una colección de registros de IIS a una regla de recopilación de datos existente

1. En la barra de búsqueda de Azure Portal, escribe **Monitor** y selecciona **Monitor** en la lista de resultados.
1. En la página **Monitor**, en la sección **Configuración**, elige **Reglas de recopilación de datos**.
1. Elige la regla **WinVMDRC** en rg-alpha.
1. En **Configuración**, elige **Orígenes de datos**.
1. En la página **Orígenes de datos**, elige **Agregar**.
1. En la página **Agregar origen de datos**, selecciona **Registros de IIS**.
1. Elija **Siguiente**.
1. En la página **Destino**, configura estos valores:

    | Propiedad | Valor    |
    |:---------|:---------|
    | Tipo de destino  | Registros de Azure Monitor   |
    | Subscription  | Su suscripción   |
    | Cuenta o espacio de nombres  | LogAnalytics1  |

9. Elige **Agregar origen de datos**.

### Configuración de Network Connection Monitor para una máquina virtual IaaS de Linux

1. En la barra de búsqueda de Azure Portal, escribe **Network Watcher** y selecciona **Network Watcher** en la lista de resultados.
1. En **Supervisión**, elige **Monitor de conexión**.
1. En la página **Monitor de conexión**, selecciona **Crear**.
1. En la página **Datos básicos** del asistente **Crear un monitor de conexión**, proporciona la siguiente información y elige **Siguiente**.

    | Propiedad | Valor    |
    |:---------|:---------|
    | Nombre del monitor de conexión  | LinuxVMPubIP   |
    | Subscription  | Su suscripción   |
    | Region    | Este de EE. UU.  |
    | Área de trabajo | LogAnalytics1  |

5. En la página **Agregar detalles del grupo de pruebas**, escribe el nombre **LinuxIPTest** y elige **Agregar orígenes**.
1. En la página **Agregar orígenes**, selecciona **Puntos de conexión de Azure** y establece el tipo en **Virtual Machines**. Selecciona **Subred** y habilita la casilla **Linux-VM**. Selecciona **Agregar puntos de conexión**.
1. Elige **Agregar configuración de prueba**. 
1. En la página **Agregar configuración de prueba**, escribe el nombre **DefaultHTTP** y elige **Agregar configuración de prueba**.
1. Elige **Agregar destinos**. Selecciona **Puntos de conexión de Azure** y establece el tipo en **Máquinas virtuales**. Selecciona **Subred** y habilita la casilla **WS-VM1**. Selecciona **Agregar puntos de conexión**.
1. Elige **Agregar grupo de prueba**.
1. Elige **Revisar y crear** y luego, **Crear**.
