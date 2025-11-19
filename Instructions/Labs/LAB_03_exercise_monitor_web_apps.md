---
lab:
  title: 'Ejercicio: Supervisión de aplicaciones web'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tareas de aptitudes

- Habilitar Application Insights
- Deshabilitación del registro del depurador de instantáneas de .NET Core.
- Configuración de los registros HTTP de la aplicación web para que se escriban en un área de trabajo de Log Analytics
- Configuración de los datos de SQL Insights que se van a escribir en un área de trabajo de Log Analytics
- Habilitación del seguimiento de cambios de archivos y configuración para aplicaciones web

## Instrucciones del ejercicio

### Habilitar Application Insights

1. En la barra de búsqueda de Azure Portal, escriba **rg-alpha** y seleccione **rg-alpha** en la lista de resultados.
1. En la lista de elementos del grupo de recursos, elija **App Services para la aplicación web con una SQL Database**.
1. En **Supervisión**, elija **Application Insights**.
1. En la página **Application Insights**, seleccione **Activar Application Insights**.
1. En la página **Application Insights** , asegúrese de que la opción **Crear un nuevo recurso** está seleccionada y de que el área de trabajo de Log Analytics está establecida en **LogAnalytics1** y seleccione **Aplicar**.
1. En el cuadro de diálogo **Aplicar configuración de supervisión**, seleccione **Sí**.

### Deshabilitación del registro del depurador de instantáneas de .NET Core.

1. En la barra de búsqueda de Azure Portal, escriba **rg-alpha** y seleccione **rg-alpha** en la lista de resultados.
1. En la lista de elementos del grupo de recursos, elija **App Services para la aplicación web con una SQL Database**.
1. En **Supervisión**, elija **Application Insights**.
1. En **Instrumentar la aplicación**, seleccione **.NET Core** y, después, establezca la opción Depurador de instantáneas en **Desactivado**. Elija **Aplicar**.
1. En el cuadro de diálogo **Aplicar configuración de supervisión**, seleccione **Sí**.

### Configuración de los registros HTTP de la aplicación web para que se escriban en un área de trabajo de Log Analytics

1. En la barra de búsqueda de Azure Portal, escriba **rg-alpha** y seleccione **rg-alpha** en la lista de resultados.
1. En la lista de elementos del grupo de recursos, elija **App Services para la aplicación web con una SQL Database**.
1. En **Supervisión**, seleccione **Configuración de diagnóstico**.
1. En la página **Configuración de diagnóstico**, seleccione **+ Agregar configuración de diagnóstico**.
1. En la página **Configuración de diagnóstico**, elija lo siguiente y seleccione **Guardar**.

    | Propiedad | Valor    |
    |:---------|:---------|
    | Nombre de la configuración de diagnóstico  | httplogs   |
    | Categorías    | Registros de HTTP  |
    | Detalles de destino   | Envío al área de trabajo de Log Analytics  |
    | Suscripción  | Su suscripción  |
    | Área de trabajo de Log Analytics   | LogAnalytics1   |

### Configuración de los datos de SQL Insights que se van a escribir en un área de trabajo de Log Analytics

1. En la barra de búsqueda de Azure Portal, escriba **rg-alpha** y seleccione **rg-alpha** en la lista de resultados.
1. En la lista de elementos del grupo de recursos, elija la base de datos SQL de ejemplo.
1. En **Supervisión**, seleccione **Configuración de diagnóstico**.
1. En la página **Configuración de diagnóstico**, seleccione **Agregar configuración de diagnóstico**.
1. En la página **Configuración de diagnóstico**, proporcione la información siguiente y seleccione **Guardar**.

    | Propiedad | Valor    |
    |:---------|:---------|
    | Nombre de la configuración de diagnóstico  | InsightLogAnalytics   |
    | Categorías    | SQL Insights  |
    | Detalles de destino   | Envío al área de trabajo de Log Analytics  |
    | Suscripción  | Su suscripción  |
    | Área de trabajo de Log Analytics   | LogAnalytics1   |
