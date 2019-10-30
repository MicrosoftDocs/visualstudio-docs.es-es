---
title: Plantilla de proyecto de servicio de nube de Azure para Python
description: Visual Studio proporciona plantillas para los servicios en la nube de Azure escritas en Python, que incluyen la implementación de roles, dependencias y solución de problemas.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 4d205ee2bbc0a6e9c44c34f3b0487abb4f22283e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983661"
---
# <a name="azure-cloud-service-projects-for-python"></a>Proyectos de servicio en la nube de Azure para Python

Visual Studio proporciona plantillas para ayudarle a empezar a crear Azure Cloud Services con Python.

Un [servicio en la nube](/azure/cloud-services/) consta de cualquier número de *roles de trabajo* y *roles web*, cada uno de los cuales realiza una tarea conceptualmente independiente, pero se puede replicar por separado entre máquinas virtuales según sea necesario para escalar. Los roles web proporcionan hospedaje para aplicaciones web de front-end. En lo que se refiere a Python, se puede usar cualquier marco web que admita WSGI para escribir este tipo de aplicación (tal como admite la [plantilla Proyecto web](python-web-application-project-templates.md)). Los roles de trabajo están pensados para procesos de larga ejecución que no interactúan directamente con los usuarios. Suelen usar los paquetes del paquete "azure", que se instala con [`pip install azure`](https://pypi.org/project/azure).

Este artículo contiene detalles sobre la plantilla de proyecto y otra compatibilidad en Visual Studio 2017 y versiones posteriores (las versiones anteriores son similares, pero con algunas diferencias). Para más información sobre el trabajo con Azure desde Python, visite el [Centro para desarrolladores de Python para Azure](/azure/python/).

## <a name="create-a-project"></a>Crear un proyecto

1. Instale el [SDK de Azure .NET para Visual Studio](https://visualstudio.microsoft.com/vs/azure-tools/), que se necesita para usar la plantilla de servicios en la nube.
1. En Visual Studio, seleccione **Archivo** > **Nuevo** > **Proyecto**, busque "Azure Python" y seleccione **Servicio en la nube Azure** en la lista:

    ![Plantilla de proyectos en la nube de Azure para Python](media/template-azure-cloud-project.png)

1. Seleccione uno o varios roles para incluir. Los proyectos en la nube pueden combinar roles escritos en diferentes lenguajes, por lo que puede escribir fácilmente cada parte de la aplicación en el lenguaje más adecuado. Para agregar nuevos roles al proyecto después de completar este cuadro de diálogo, haga clic con el botón derecho en **Roles** en el **Explorador de soluciones** y seleccione uno de los elementos bajo **Agregar**.

    ![Incorporación de roles en la plantilla de proyectos en la nube de Azure](media/template-azure-cloud-service-project-wizard.png)

1. Cuando se crean los proyectos de rol individuales, es posible que se le pida instalar paquetes de Python adicionales, como los marcos de Django, Bottle o Flask si ha seleccionado un rol que utiliza uno de ellos.

1. Después de agregar un nuevo rol al proyecto, aparecen instrucciones de configuración. Los cambios de configuración son normalmente innecesarios, pero pueden resultar útiles para una futura personalización de los proyectos. Tenga en cuenta que al agregar varios roles al mismo tiempo, solo permanecen abiertas las instrucciones para el último rol. Sin embargo, puede encontrar las instrucciones y sugerencias para solucionar problemas en sus archivos *readme.mht* correspondientes, que se encuentran en la raíz del rol o en la carpeta *bin*.

1. Una carpeta *bin* de proyecto también contiene uno o dos scripts de PowerShell que se usan para configurar la máquina virtual remota, incluida la instalación de Python, cualquier archivo [*requirements.txt*](#dependencies) del proyecto y la configuración de IIS si es necesario. Puede editar estos archivos como desee para la implementación, aunque las opciones más comunes se pueden administrar de otras maneras (vea [Configuración de la implementación de roles](#configure-role-deployment) a continuación). No se recomienda quitar estos archivos, ya que, en su lugar, se usa un script de configuración heredado si los archivos no están disponibles.

    ![Archivos de compatibilidad de rol de trabajo](media/template-azure-cloud-service-worker-role-support-files.png)

    Para agregar estos scripts de configuración a un nuevo proyecto, haga clic con el botón derecho en el proyecto, seleccione **Agregar** > **Nuevo elemento** y seleccione **Archivos auxiliares de rol web** o **Archivos auxiliares de rol de trabajo**.

## <a name="configure-role-deployment"></a>Configuración de la implementación de roles

Los scripts de PowerShell de una carpeta *bin* del proyecto de rol controlan la implementación de ese rol y se pueden editar para personalizar la configuración:

- *ConfigureCloudService.ps1* se utiliza para roles web y de trabajo, normalmente para instalar y configurar dependencias establecer la versión de Python.
- *LaunchWorker.ps1* se utiliza únicamente para roles de trabajo y se usa para cambiar el comportamiento de inicio, agregar argumentos de línea de comandos o agregar variables de entorno.

Ambos archivos contienen instrucciones para personalización. También puede instalar su propia versión de Python mediante la incorporación de otra tarea en el archivo *ServiceDefinition.csdef* del proyecto de servicios en la nube principal, estableciendo la variable `PYTHON` en su ruta de acceso *python.exe* instalada (o equivalente). Cuando se establece `PYTHON`, Python no se instala desde NuGet.

Se puede realizar una configuración adicional como se indica a continuación:

1. Instale paquetes con `pip` actualizando el archivo *requirements.txt* en el directorio raíz del proyecto. El script *ConfigureCloudService.ps1* instala este archivo en la implementación.
1. Establezca variables de entorno modificando su archivo *web.config* (roles web) o la sección `Runtime` de su archivo *ServiceDefinition.csdef* (roles de trabajo).
1. Especifique el script y los argumentos que se van a utilizar para un rol de trabajo mediante la modificación de la línea de comandos en la sección `Runtime/EntryPoint` del archivo *ServiceDefinitions.csdef*.
1. Establezca el script del controlador principal para un rol web a través del archivo *web.config*.

## <a name="test-role-deployment"></a>Prueba de la implementación de roles

Mientras escribe los roles, puede probar el proyecto en la nube localmente usando el emulador de servicios en la nube. El emulador se incluye con las herramientas del SDK de Azure y es una versión limitada del entorno usado cuando el servicio en la nube se publica en Azure.

Para iniciar el emulador, asegúrese en primer lugar de que el proyecto en la nube es el proyecto de inicio de la solución haciendo clic con el botón derecho y seleccionando **Establecer como proyecto de inicio**. A continuación, seleccione **Depurar** > **Iniciar depuración** (**F5**) o **Depurar** > **Iniciar sin depurar** (**Ctrl**+**F5**).

Tenga en cuenta que, debido a las limitaciones del emulador, no es posible depurar el código Python. Por tanto, le recomendamos que depure los roles ejecutándolos independiente y, luego, use el emulador para las pruebas de integración antes de la publicación.

## <a name="deploy-a-role"></a>Implementación de un rol

Para abrir el asistente **Publicar**, seleccione el proyecto de rol en el **Explorador de soluciones** y seleccione **Compilar** > **Publicar** en el menú principal, o haga clic con el botón derecho en el proyecto y seleccione **Publicar**.

El proceso de publicación consta de dos fases. En primer lugar, Visual Studio crea un único paquete que contiene todos los roles del servicio en la nube. Este paquete es lo que se implementa en Azure, que inicializa una o varias máquinas virtuales para cada rol e implementa el origen.

A medida que cada máquina virtual se activa, ejecuta el script *ConfigureCloudService.ps1* e instala todas las dependencias. Este script instala de manera predeterminada una versión reciente de Python desde [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) y todos los paquetes especificados en un archivo *requirements.txt*.

Por último, los roles de trabajo ejecutan *LaunchWorker.ps1*, que comienza a ejecutar el script de Python; los roles web inicializan IIS y empiezan a controlar las solicitudes web.

## <a name="dependencies"></a>Dependencias

Para Cloud Services, el script *ConfigureCloudService.ps1* usa `pip` para instalar un conjunto de dependencias de Python. Las dependencias se deben especificar en un archivo denominado *requirements.txt* (personalizable modificando *ConfigureCloudService.ps1*). El archivo se ejecuta con `pip install -r requirements.txt` como parte de la inicialización.

Tenga en cuenta que las instancias del servicio en la nube no incluyen compiladores de C, por lo que todas las bibliotecas con extensiones de C deben proporcionar binarios previamente compilados.

pip y sus dependencias, así como los paquetes de *requirements.txt*, se descargan automáticamente y pueden contar como uso de ancho de banda facturable. Vea [Administración de los paquetes necesarios con requirements.txt](managing-required-packages-with-requirements-txt.md) para obtener información sobre cómo administrar archivos *requirements.txt*.

## <a name="troubleshooting"></a>Solución de problemas

Si el rol web o de trabajo no se comporta correctamente después de la implementación, compruebe lo siguiente:

- El proyecto de Python incluye una carpeta*bin\\* con (como mínimo):

  - *ConfigureCloudService.ps1*
  - *LaunchWorker.ps1* (para roles de trabajo)
  - *ps.cmd*

- El proyecto de Python incluye un archivo *requirements.txt* que enumera todas las dependencias (o como alternativa, una colección de archivos de rueda).
- Habilite Escritorio remoto en el servicio en la nube e investigue los archivos de registro.
- Los registros para *ConfigureCloudService.ps1* y *LaunchWorker.ps1* se almacenan en la carpeta *C:\Resources\Directory\%RoleId%.DiagnosticStore\LogFiles* en el equipo remoto.
- Los roles web pueden escribir registros adicionales en una ruta de acceso configurada en *web.config*; es decir, la ruta de acceso en appSetting `WSGI_LOG`. La mayoría del registro de IIS o FastCGI convencional también funciona.
- Actualmente, el archivo *LaunchWorker.ps1.log* es la única manera de ver la salida o los errores que muestra el rol de trabajo de Python.
