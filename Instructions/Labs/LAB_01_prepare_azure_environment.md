---
lab:
  title: Preparar el entorno de Azure
  module: Guided Project - Deploy and configure Azure Monitor
---

## Preparar la suscripción de tipo bring-your-own-subscription (BYOS)

Este conjunto de ejercicios de laboratorio presupone que tienes permisos de administrador global para una suscripción a Azure.

1. En la ventana de búsqueda de Azure Portal, escribe **Grupos de recursos** y selecciona **Grupos de recursos** en los resultados de la búsqueda.
1. En la página **Grupos de recursos**, selecciona **Crear**.
1. En la página **Crear un grupo de recursos**, selecciona tu suscripción y escribe el nombre rg-alpha. Establece la región en Este de EE. UU., elige **Revisar y crear** y, luego, **Crear**.

> [!NOTE]
> Este conjunto de ejercicios asume que quieres implementar en la región Este de EE. UU., pero puedes cambiarlo a otra región de tu elección. Recuerda que, cada vez que se mencione Este de EE. UU. en estas instrucciones, deberás sustituirlo por la región que hayas elegido.

## Creación del grupo de seguridad de examinadores del registro de aplicaciones

En este ejercicio, crearás un grupo de seguridad de Entra ID.

1. En la barra de búsqueda de Azure Portal, escribe Azure Active Directory (o Entra ID) y elige esta opción en la lista de resultados.
1. En la página **Directorio predeterminado**, selecciona **Grupos**.
1. En la página **Grupos**, selecciona **Nuevo grupo**.
1. En la página **Nuevo grupo**, proporciona los valores de la tabla siguiente y elige **Crear**.


    | Propiedad | Valor    |
    |:---------|:---------|
    | Tipo de grupo  | Seguridad   |
    | Nombre del grupo  | Examinadores del registro de aplicaciones   |
    | Descripción del grupo  | Examinadores del registro de aplicaciones   |


## Implementación y configuración de WS-VM1

En este ejercicio, implementarás y configurarás una máquina virtual de Windows Server.

1. En la barra de búsqueda de Azure Portal, escribe **Máquinas virtuales** y selecciona **Máquinas virtuales** en los resultados de la búsqueda.
1. En la página **Máquinas virtuales**, selecciona **Crear** y luego **Máquina virtual de Azure**.
1. En la página **Datos básicos** del asistente para crear una máquina virtual, selecciona los siguientes valores y luego elige **Revisar y crear**.

    | Propiedad | Valor    |
    |:---------|:---------|
    | Suscripción  | Su suscripción   |
    | Grupo de recursos    | rg-alpha  |
    | Nombre de la máquina virtual  | WS-VM1   |
    | Region    | Este de EE. UU.  |
    | Opciones de disponibilidad  | No se requiere redundancia de la infraestructura  |
    | Tipo de seguridad | Estándar   |
    | Imagen | Windows Server 2022 Datacenter: Azure Edition – x64 Gen2  |
    | Arquitectura VM   | x64  |
    | Size  | Standard_D4s_v3 – 4 vCPU, 16 GiB de memoria  |
    | Cuenta de administrador | prime  |
    | Contraseña  | [Seleccionar una contraseña segura única] P@ssw0rdP@ssw0rd   |
    | Puertos de entrada | RDP 3389   |

4. Revise la configuración y seleccione **Crear**.
1. Espere a que la implementación se complete. Cuando finalice la implementación, selecciona **Ir al recurso**.
1. En la página **Propiedades de WS-VM1**, elige **Redes**.
1. En la página **Redes**, selecciona la regla RDP. 
1. En el espacio de reglas de RDP, cambia el Origen a Mi dirección IP y elige **Guardar**.

    Esto restringe las conexiones RDP entrantes a la dirección IP que estés usando actualmente.

9. En la página **Redes**, elige **Agregar regla de puerto de entrada**.
1. En la página **Agregar regla de seguridad de entrada**, configura los valores siguientes y elige **Agregar**.

    | Propiedad | Valor    |
    |:---------|:---------|
    | Source  | Cualquiera  |
    | Source port ranges    | *   |
    | Destination  | Any   |
    | Servicio   | HTTP  |
    | Acción    | Permitir  |
    | Prioridad  | 310   |
    | Nombre  | AllowAnyHTTPInbound  |

11. En la página **WS-VM1**, elige **Conectar**.
1. En RDP nativo, elige **Seleccionar**.
1. En la página **RDP nativo**, elige **Descargar archivo RDP** y luego abre el archivo. Al abrir el archivo RDP, se abre el cuadro de diálogo Conexión a escritorio remoto.
1. En el cuadro de diálogo **Seguridad de Windows**, selecciona **Más opciones** y luego elige Usar otra cuenta.
1. Escribe el nombre de usuario como .\prime y la contraseña como la contraseña segura que elegiste en el paso 3. Luego elige **Aceptar**.
1. Cuando hayas iniciado sesión en la máquina virtual de Windows Server, haz clic con el botón derecho en la sugerencia **Inicio** y luego elige **Windows PowerShell (Administrador)**.
1. En el símbolo del sistema con privilegios elevados, escribe el siguiente comando y presiona **Entrar**.
    Install-WindowsFeature Web-Server  -IncludeAllSubFeature -IncludeManagementTools 
1. Cuando se complete la instalación, ejecuta el siguiente comando para cambiar al directorio raíz del servidor web.
    cd c:\inetpub\wwwroot\
1. Ejecute el siguiente comando:
    Wget https://raw.githubusercontent.com/Azure-Samples/html-docs-hello-world/master/index.html -OutFile index.html


## Implementación y configuración de LX-VM2

En este ejercicio, crearás y configurarás una máquina virtual de Linux.

1. En la barra de búsqueda de Azure Portal, escribe **Máquinas virtuales** y selecciona **Máquinas virtuales** en los resultados de la búsqueda.
1. En la página **Máquinas virtuales**, selecciona **Crear** y luego **Máquina virtual de Azure**.
1. En la página **Datos básicos** del asistente para crear una máquina virtual, selecciona los siguientes valores y luego elige **Revisar y crear**.

    | Propiedad | Valor    |
    |:---------|:---------|
    | Suscripción  | Su suscripción   |
    | Grupo de recursos    | rg-alpha  |
    | Nombre de la máquina virtual  | Linux-VM2   |
    | Region    | Este de EE. UU.  |
    | Opciones de disponibilidad  | No se requiere redundancia de la infraestructura  |
    | Tipo de seguridad | Estándar   |
    | Imagen | Ubuntu Server 20.04 LTS – x64 Gen2  |
    | Arquitectura VM   | x64  |
    | Size  | Standard_D2s_v3 – 2 vCPU, 8 GiB de memoria  |
    | Tipo de autenticación   | Contraseña  |
    | Nombre de usuario  | Prime   |
    | Contraseña  | [Seleccionar una contraseña segura única] P@ssw0rdP@ssw0rd   |
    | Puertos de entrada públicos  | Ninguno   |

4. Revisa la información y elige **Crear**.
1. Una vez implementada la máquina virtual, abre la página **Propiedades de VM** y elige **Extensiones y aplicaciones** en **Configuración**.
1. Elige **Agregar** y selecciona el **Agente de Network Watcher para Linux**. Elige **Siguiente** y luego **Revisar y crear**. Elija **Crear**.
1. Configura la extensión AzureNetworkWatcherExtension y OmsAgentForLinux para que se actualicen automáticamente.


## Implementación de una aplicación web con una instancia de SQL Database

1. Asegúrate de que sigues con la sesión iniciada en Azure Portal.
1. Abre una nueva pestaña en el explorador y navega hasta https://github.com/Azure/azure-quickstart-templates/tree/master/quickstarts/microsoft.web/web-app-sql-database
1. En la página de GitHub, elige **Implementar en Azure**.
1. Se abrirá una nueva pestaña. Si fuera necesario, vuelve a iniciar sesión en Azure con la cuenta que tenga privilegios de administrador global.
1. En la página **Datos básicos**, selecciona **Editar plantilla**.
1. En el editor de la plantilla, elimina el contenido de las líneas 158 a 174, ambas inclusive, y elimina la "," en la línea 157. Elija **Guardar**.
1. En la página **Datos básicos**, proporciona la información siguiente y elige **Siguiente**.

    | Propiedad | Valor    |
    |:---------|:---------|
    | Suscripción  | Su suscripción   |
    | Grupo de recursos    | rg-alpha  |
    | Region    | Este de EE. UU.  |
    | Nombre de SKU  | F1  |
    | Capacidad de SKU  | 1   |
    | Inicio de sesión de administrador de SQL   | prime  |
    | Contraseña de inicio de sesión de administrador de SQL  | [Seleccionar una contraseña segura única] P@ssw0rdP@ssw0rd   |

8. Revisa la información presentada y selecciona **Crear**.
1. Una vez finalizada la implementación, elige **Ir al grupo de recursos**.

## Implementación de una aplicación web en Linux

1. Asegúrate de que sigues con la sesión iniciada en Azure Portal.
1. Abre una nueva pestaña en el explorador y ve a https://learn.microsoft.com/en-us/samples/azure/azure-quickstart-templates/webapp-basic-linux/
1. En la página de GitHub, elige **Implementar en Azure**.
1. En la página **Datos básicos**, proporciona la información siguiente y elige **Siguiente**.

    | Propiedad | Valor    |
    |:---------|:---------|
    | Suscripción  | Su suscripción   |
    | Grupo de recursos    | rg-alpha  |
    | Region    | Este de EE. UU.  |
    | Nombre de la aplicación web  | AzureLinuxAppWXYZ (asigna un número aleatorio a los cuatro caracteres finales del nombre)  |
    | SKU   | S1   |
    | Versión de Linux Fx  | php|7.4  |

5. Revisa la información y elige **Crear**.
