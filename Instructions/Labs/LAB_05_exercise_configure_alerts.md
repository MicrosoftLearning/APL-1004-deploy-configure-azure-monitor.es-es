---
lab:
  title: 'Ejercicio: Configuración de alertas'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tareas de aptitudes

- Crear un grupo de acciones para enviar un correo electrónico
- Crear una alerta para el uso de CPU de la máquina virtual

## Instrucciones del ejercicio

### Crear un grupo de acciones para enviar un correo electrónico

1. En la barra de búsqueda de Azure Portal, escriba **Supervisión** y, después, seleccione **Supervisión** en la lista de resultados.
1. En el menú de navegación, seleccione **Alertas**.
1. Seleccione **Grupo de acciones**.
1. En la página **Grupos de acciones**, seleccione **Crear**.
1. En la página **Datos básicos** del asistente para crear grupos de acciones, establezca la siguiente configuración y seleccione **Siguiente**.

    | Propiedad | Valor    |
    |:---------|:---------|
    | Suscripción  | Su suscripción   |
    | Grupo de recursos  | rg-alpha   |
    | Region    | Global  |
    | Nombre del grupo de acciones | NotifyCPU  |
    | Nombre  | NotifyCPU  |

6. En la página **Notificaciones**, establezca el tipo de notificación en **Correo electrónico/Mensaje SMS/Notificaciones push/Voz** y asigne el nombre **NotificationEmail**. Seleccione el icono de lápiz **Editar**.
1. En la casilla Correo electrónico/Mensaje SMS/Notificaciones push/Voz, habilite la casilla **Correo electrónico** y escriba la dirección **prime@fabrikam.com**. Elija **Aceptar**. 
1. Seleccione **Revisar y crear**. Seleccione **Crear**.


### Crear una alerta para el uso de CPU de la máquina virtual

1. En la barra de búsqueda de Azure Portal, escriba **rg-alpha** y seleccione **rg-alpha** en la lista de resultados.
1. En la lista de elementos del grupo de recursos, seleccione **Linux-VM2**.
1. En la página **Propiedades de Linux-VM2**, seleccione **Alertas** en **Supervisión**.
1. En la página **Alertas**, seleccione **Crear** y, después, seleccione **Regla de alertas**.
1. En la página **Condición** del asistente para crear una regla de alertas, establezca el nombre de Señal como **Percentage CPU**. Use la configuración predeterminada y haga clic en **Siguiente**.
1. En la página **Acciones**, seleccione **Seleccionar grupo de acciones**.
1. En la página **Seleccionar grupo de acciones**, elija **NotifyCPU** y elija **Seleccionar**.
1. Escriba el nombre de la alerta **HighCPU** en la página **Detalles**. Seleccione **Revisar y crear** y, después, seleccione **Crear**.

## Limpieza de una suscripción

Para limpiar la suscripción, elimine el grupo de recursos **rg-alpha** y elimine el grupo de seguridad **Examinadores de registros de aplicaciones**.
