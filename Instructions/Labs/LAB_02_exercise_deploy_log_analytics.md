---
lab:
  title: 'Ejercicio: Implementación de Log Analytics'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tareas de aptitudes

- Creación de un área de trabajo de Log Analytics
- Configuración de las directivas de archivo y retención de datos de Log Analytics
- Habilite el acceso a un área de trabajo de Log Analytics.

## Instrucciones del ejercicio

### Creación de un área de trabajo de Log Analytics

1. En la barra de búsqueda de Azure Portal, escriba **Log Analytics** y, después, seleccione **Áreas de trabajo de Log Analytics** en los resultados.
1. En la página **Áreas de trabajo de Log Analytics**, seleccione **Crear**.
1. En la página **Datos básicos** del asistente para crear una área de trabajo de Log Analytics, seleccione la siguiente información y, después, elija **Revisar y crear**.
   
    | Propiedad | Valor    |
    |:---------|:---------|
    | Suscripción  | Su suscripción   |
    | Grupo de recursos    | rg-alpha  |
    | Nombre  | LogAnalytics1  |
    | Region    | Este de EE. UU.  |

4. Revise la información y seleccione **Crear**.

### Configuración de las directivas de archivo y retención de datos de Log Analytics

1. En la barra de búsqueda de Azure Portal, escriba **Log Analytics** y, después, seleccione **Áreas de trabajo de Log Analytics** en los resultados.
1. En la página **Áreas de trabajo de Log Analytics**, seleccione **+ LogAnalytics1**.
1. En la página **Área de trabajo de Log Analytics** de LogAnalytics1, seleccione **Uso y costes estimados**.
1. Seleccione **Retención de datos** y establezca el control deslizante en 60 días. Elija **Aceptar**.
1. En la página **Área de trabajo de Log Analytics** de LogAnalytics1, seleccione **Uso y costes estimados**.
1. Seleccione **Límite diario**. Seleccione **Activado**. Establezca el límite diario en 10 GB y seleccione **Aceptar**.

### Habilite el acceso a un área de trabajo de Log Analytics.

1. En la barra de búsqueda de Azure Portal, escriba **Log Analytics** y, después, seleccione **Áreas de trabajo de Log Analytics** en los resultados.
1. En la página **Áreas de trabajo de Log Analytics**, seleccione **+ LogAnalytics1**.
1. Seleccione **Access Control (IAM)** .
1. Seleccione **Agregar** y, después, **Agregar asignación de roles**.
1. En la lista de roles, seleccione **Lector de Log Analytics** y seleccione **Siguiente**.
1. En la página **Miembros**, elija **Seleccionar miembros** y seleccione el grupo de seguridad Examinadores de registros de aplicaciones. **Elija Seleccionar**.
1. En el espacio **Miembros**, seleccione **Revisar y asignar**.
