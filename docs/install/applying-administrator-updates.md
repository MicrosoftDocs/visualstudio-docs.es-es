---
title: Aplicación de actualizaciones de administrador a Visual Studio con Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Obtenga información sobre cómo aplicar actualizaciones de administrador a Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d316fc35df8c571a9112d7a653737e099df80559
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547458"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Aplicación de actualizaciones de administrador que usan Microsoft Endpoint Configuration Manager

En este documento se describen los distintos tipos y características de las actualizaciones de administrador de Visual Studio. A continuación, encontrará información sobre cómo y cuándo deben distribuirse en toda la organización, qué opciones de configuración están disponibles y cómo ver informes y solucionar problemas. Para obtener más información acerca de los requisitos previos para el uso de actualizaciones de administrador, consulte [Habilitación de las actualizaciones de administrador](../install/enabling-administrator-updates.md).

## <a name="understanding-visual-studio-administrator-updates"></a>Descripción de las actualizaciones de administrador de Visual Studio 

El paquete de actualizaciones del administrador de Visual Studio que se publica en Microsoft Update para su uso por el catálogo de Microsoft y WSUS contiene la información que necesita Configuration Manager para poder descargar y distribuir la actualización de Visual Studio a los equipos cliente. También contiene información que necesita un administrador de TI para decidir qué actualizaciones distribuir en toda la organización, y facilita el mantenimiento de los diseños de red. Los paquetes de actualización del administrador de Visual Studio no contienen suficiente información para realizar una instalación nueva del producto, ni contienen ninguno de los archivos binarios reales del producto que se publican en Content Delivery Network. Las actualizaciones del administrador de Visual Studio son acumulativas, al igual que las actualizaciones habituales de Visual Studio. Puede suponer que cualquier actualización de Visual Studio que tenga un número de versión de producto superior y una fecha de lanzamiento posterior es un superconjunto de una versión anterior más antigua. 

Las actualizaciones de administrador de Visual Studio se aplican a las versiones de servicio de Visual Studio que se encuentran en servicio de soporte técnico. Para obtener más información sobre qué líneas de base de servicio de Visual Studio todavía se admiten durante un período de tiempo determinado, consulte [Ciclo de vida y mantenimiento del producto de Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs). Todas las líneas de base de servicio de Visual Studio compatibles se mantendrán seguras.  

## <a name="types-and-characteristics-of-administrator-updates"></a>Tipos y características de las actualizaciones de administrador 

Hay tres tipos de actualizaciones de administrador para Visual Studio:

* Las **actualizaciones de seguridad** se aplican a todas las ediciones de Visual Studio (por ejemplo, Enterprise, Professional, Community, etc.) y contienen cambios de nivel de servicio limitados, muy dirigidos y compatibles. Las actualizaciones de seguridad no harán avanzar a un cliente a una versión secundaria posterior; están diseñadas para distribuir correcciones a las vulnerabilidades de seguridad para un cliente que ya está en un nivel de versión secundaria particular. Las actualizaciones de seguridad tendrán al menos una corrección de seguridad en ellas, pero la corrección de seguridad puede estar en un componente o carga de trabajo instalado en el equipo cliente. Por ejemplo, podríamos corregir una vulnerabilidad de seguridad en los componentes de .NET, y etiquetaremos la actualización como una actualización de seguridad, pero realmente no tendría ningún efecto significativo en un equipo cliente que tuviera solo componentes de C++ instalados. Las actualizaciones de seguridad también pueden contener otras correcciones de confiabilidad u otras actualizaciones de componentes necesarias. Las actualizaciones de seguridad se publican en el [catálogo de Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) y [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus), donde se clasifican como "Actualizaciones de seguridad".
 
* Las **actualizaciones de características** permiten a los administradores de TI hacer avanzar los equipos de su organización a una versión secundaria más reciente de Visual Studio 2019. Las actualizaciones de características solo se aplican a las ediciones de Visual Studio que se encuentran normalmente en empresas, como las SKU de Enterprise, Professional y Build Tools. Todas las actualizaciones de características se publicarán en el catálogo de Microsoft Update como "Paquetes de características" y estarán disponibles para [importarlas manualmente en Configuration Manager desde el catálogo de Microsoft Update](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog). Las actualizaciones de características son acumulativas y contendrán correcciones adicionales de calidad y de seguridad anteriores. Vea la [sección de las opciones de configuración](#understanding-configuration-options) más adelante para obtener instrucciones sobre cómo configurar un equipo cliente para que permanezca en una línea de base de servicio y evitar que se distribuyan las actualizaciones de características a clientes específicos. 

* Las **actualizaciones de calidad** también se aplican a las ediciones de Visual Studio que se encuentran normalmente en las empresas, y contienen cambios de nivel servicio limitados, muy específicos y compatibles. Las actualizaciones de calidad no harán avanzar a un cliente a una versión secundaria posterior; están diseñadas para ofrecer correcciones de rendimiento y fiabilidad u otras actualizaciones de componentes necesarias para un cliente que ya se encuentra en un nivel de versión secundaria concreto. Las actualizaciones de calidad se acumulan junto con las de seguridad, por lo que contendrán correcciones de seguridad solo si la corrección de seguridad ya se ha publicado de forma independiente. Las actualizaciones de calidad se publican en el catálogo de Microsoft Update como "Actualizaciones", y también están disponibles para [importarlas manualmente en Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog).

### <a name="decoding-the-titles-of-administrator-updates"></a>Descodificación de los títulos de las actualizaciones de administrador

El título de cada actualización de administrador describe el intervalo de versiones aplicable y la versión resultante de la actualización.Por ejemplo,

::: moniker range="vs-2017"

* **La actualización de Visual Studio 2017 de la versión 15.9.0 a la 15.9.35**, clasificada como "Actualización de seguridad", se aplicará a cualquier edición de Visual Studio 2017 en el cliente entre las versiones 15.9.0 y 15.9.35, y actualizará esas ediciones del cliente a la 15.9.35.

* **La actualización de Visual Studio 2017 de la versión 15.0.0 a la 15.9.0**, clasificada como un "Paquete de características", se aplicará a las ediciones de Visual Studio 2017 con licencia para uso empresarial en el cliente entre todo el intervalo de versiones de producto de 15.0.0 a 15.9.0 y actualizará esas ediciones de cliente a la 15.9.0. La aplicación de este Paquete de características permite, básicamente, que los clientes reciban actualizaciones de seguridad. 

* **La actualización de Visual Studio 2017 de la versión 15.9.0 a la 15.9.37**, clasificada simplemente como "Actualizaciones", se aplicará a las ediciones de Visual Studio 2017 con licencia para uso empresarial en el cliente entre las versiones 15.9.0 y 15.9.37, y actualizará esas ediciones del cliente a la 15.9.37. 

::: moniker-end

::: moniker range="vs-2019"

* **La actualización de Visual Studio 2019 de la versión 16.7.0 a la 16.7.12**, clasificada como "Actualización de seguridad", se aplicará a cualquier edición de Visual Studio 2019 en el cliente entre las versiones 16.7.0 y 16.7.12, y actualizará esas ediciones del cliente a la 16.7.12.  

* **La actualización de Visual Studio 2019 de la versión 16.0.0 a la 16.9.0**, clasificada como "Paquete de características", se aplicará a las ediciones de Visual Studio 2019 con licencia para uso empresarial en el cliente entre todo el intervalo de versiones del producto, de la 16.0.0 a la 16.9.0, y actualizará esas ediciones del cliente, que no se hayan configurado para permanecer en una línea de base de servicio anterior, a la 16.9.0. 

* **La actualización de Visual Studio 2019 de la versión 16.8.0 a la 16.8.7**, clasificada simplemente como "Actualizaciones", se aplicará a las ediciones de Visual Studio 2019 con licencia para uso empresarial en el cliente entre las versiones 16.8.0 y 16.8.7, y actualizará esas ediciones del cliente a la 16.8.7. 

::: moniker-end

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Uso de Configuration Manager para implementar actualizaciones de Visual Studio

### <a name="understanding-configuration-options"></a>Descripción de las opciones de configuración

Hay algunas opciones de configuración que se pueden usar para personalizar las actualizaciones del administrador de Visual Studio de modo que sean compatibles con los requisitos de implementación y preferencias de su organización y estén en consonancia con ellos. Las opciones de configuración más comunes se enumeran a continuación. Para obtener una lista exhaustiva de todos los comportamientos de actualización de administrador admitidos, consulte [Uso de parámetros de la línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) y preste atención solo a los que corresponden a la acción "update".

* **[Participación en las actualizaciones de administrador](../install/enabling-administrator-updates.md#encoding-administrator-intent-on-the-client-machines)** : esta clave del Registro es necesaria para que el equipo del cliente reciba actualizaciones de administrador. Es una clave para todo el equipo, lo que significa que se aplica a todas las instancias de Visual Studio instaladas del cuadro. 
 
* **Optar por no recibir Visual Studio**: los usuarios de Visual Studio pueden usar una clave **AdministratorUpdatesOptOut** independiente para *no recibir* actualizaciones administrador de Visual Studio. El propósito de esta clave es permitir que el usuario de Visual Studio tenga algún control sobre la aplicación automática de las actualizaciones a la máquina. Para configurar el equipo cliente para que bloquee las actualizaciones de administrador, establezca la clave REG_DWORD **AdministratorUpdatesOptOut** en  **1**. La ausencia de la clave, o un valor establecido de  **0**, significa que el usuario de Visual Studio desea recibir actualizaciones de administrador en Visual Studio.

    Tenga en cuenta que la clave **AdministratorUpdatesOptOut** para la codificación de las preferencias del usuario tiene prioridad sobre la clave  **AdministratorUpdatesEnabled**, que codifica la intención del administrador de TI. Si **AdministratorUpdatesOptOut** se establece en **1**, la actualización se bloqueará en el cliente, incluso si la clave **AdministratorUpdatesEnabled**   también está establecida en **1**.Esta acción supone que los administradores de TI pueden tener acceso a los desarrolladores que optan por dejar de participar y supervisarlos, y que las dos partes pueden analizar entonces las necesidades más importantes.Los administradores de TI pueden cambiar cualquier clave siempre que lo deseen.
 
* **Ubicación de los bits de producto actualizados**: la mayoría de las veces, los equipos cliente descargan los bits de producto actualizados desde Internet a través de CDN de Microsoft. Este escenario requiere que los equipos cliente tengan acceso a Internet. Sin embargo, algunas empresas limitan los equipos cliente para que solo instalen y actualicen bits desde una ubicación de diseño de red interna. Para asegurarse de que las actualizaciones de administrador se pueden aplicar mediante bits actualizados que se encuentran en una ubicación de red interna, deben cumplirse las siguientes condiciones antes de que se pueda implementar correctamente la actualización del administrador: 

  - El equipo del cliente debe, en algún momento, haber ejecutado el programa previo desde esa ubicación de diseño de red. Idealmente, la instalación del cliente original habría sucedido con el programa previo del diseño de red, pero también es posible instalar una actualización con un programa previo actualizado en esa misma ubicación de red. Cualquiera de estas acciones insertaría en el equipo del cliente una conexión con esa ubicación de diseño concreta.   
  - La ubicación de diseño de red a la que está conectado el cliente debe estar [actualizada para que contenga los bits de producto actualizados](../install/update-a-network-installation-of-visual-studio.md) que la actualización de administrador quiere implementar. 

::: moniker range="vs-2019"

* **Adherencia a la línea de base de servicio**: como se describió anteriormente, las actualizaciones de administrador que son actualizaciones de características adelantan una instalación de Visual Studio a una versión secundaria más actual del producto. A veces, sin embargo, a los equipos de desarrollo les gusta permanecer en un determinado nivel de línea de base de servicio estable y seguro, y les gusta controlar cuándo sus clientes avanzan a una versión secundaria más actual. Para configurar un equipo cliente para que permanezca en una línea de base de servicio e ignore las actualizaciones de características de administrador no deseadas que se le envían, deberá crear y establecer el valor de datos **BaselineStickinessVersions2019** Reg_SZ a una cadena que represente las líneas de base permitidas en las que el equipo cliente pueda ajustarse y permanecer.  La cadena puede contener una secuencia de versiones de línea de base de servicio separadas por comas, como **16.4.0,16.7.0**. Se puede incluir cualquier número de versiones de línea de base de servicio en la cadena, y también se admite la palabra **All**, que es una abreviatura para hacer referencia a todas las líneas de base de servicio admitidas. 

     Si el valor del Registro `BaselineStickinessVersions2019` tiene un formato incorrecto, se bloqueará la instalación de todas las actualizaciones de características en el equipo. Además, preste atención a los [períodos de tiempo admitidos para las actualizaciones de características de Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs). Aunque es técnicamente posible aplicar actualizaciones de características que han alcanzado el final de su ciclo de vida, no se recomienda porque estarán fuera del soporte técnico y, por lo tanto, serán potencialmente inseguras.

::: moniker-end

* **Forzar que se produzca la actualización incluso si Visual Studio está en uso**: Visual Studio debe cerrarse antes de instalar la actualización. Si Visual Studio está abierto o en uso, se anulará la instalación de la actualización. Una manera sencilla de asegurarse de que Visual Studio está cerrado es configurar Configuration Manager para aplicar la actualización justo después de reiniciar el equipo. También puede usar el parámetro `--force` para forzar el cierre de Visual Studio. Forzar el cierre de Visual Studio puede provocar la pérdida de trabajo, por lo que debe usarse con precaución. La ejecución de una actualización de administrador en el contexto del sistema predeterminado omitirá la marca `–-force`, por lo que tendrá que configurar la actualización del administrador para que se ejecute en el contexto del usuario.

### <a name="methods-for-configuring-an-administrator-update"></a>Métodos para configurar una actualización de administrador

Hay tres métodos principales para configurar las actualizaciones de administrador: una clave del Registro, un archivo de configuración en el equipo cliente o una modificación del propio paquete de implementación de Configuration Manager.   

* **Clave del Registro**: las actualizaciones de administrador buscan claves del Registro específicas en cualquiera de las ubicaciones de Visual Studio estándar, tal como se describe en [Establecimiento de valores predeterminados para implementaciones empresariales de Visual Studio](../install/set-defaults-for-enterprise-deployments.md). Las opciones que controlan las claves del Registro son elementos como **AdministratorUpdatesOptOut** Reg_DWORD, **AdministratorUpdatesOptOut** Reg_DWORD y **BaselineStickinessVersions2019** Reg_SZ. Se requiere acceso de administrador en el equipo cliente para crear y establecer el valor de las claves del Registro. 
 
* **Archivo de configuración**: algunos ajustes pueden conservarse en el equipo cliente en un archivo de configuración opcional, lo que tiene la ventaja de establecerlo una sola vez y hacer que se aplique a todas las futuras actualizaciones del administrador. El enfoque del archivo de configuración se comporta como una clave del Registro y es para todo el equipo, lo que significa que se aplicará a todas las instalaciones de Visual Studio instaladas en el equipo cliente. La ubicación estándar del archivo de configuración se encuentra en `C:\ProgramData\Microsoft\VisualStudio\updates.config`. Sin embargo, si desea usar otra ubicación para almacenar el archivo, puede hacerlo creando una clave del Registro Reg_SZ denominada **UpdateConfigurationFile** y estableciendo el valor de esta clave en la ruta de acceso del archivo de configuración. Esta clave del Registro se puede colocar en cualquiera de las ubicaciones del Registro de Visual Studio, tal como se describe en [Establecimiento de valores predeterminados para implementaciones empresariales de Visual Studio](../install/set-defaults-for-enterprise-deployments.md). Si decide agregar un valor de Registro para una ubicación de archivo de configuración personalizada, buscará ese archivo; si el archivo no existe, se producirá una excepción y se generará un error en la actualización.    
 
     El archivo de configuración, que está en formato JSON, admite la opción `installerUpdateArgs`, que es una matriz de cadenas separadas por comas que especifican más modificadores que se pueden pasar al instalador de Visual Studio. Si el contenido del archivo incluye un campo no válido o una opción no admitida, se producirá un error en la actualización. Para obtener más información sobre él, vea la página [Usar parámetros de la línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).
 
   A continuación se muestra un ejemplo de configuración: 

   ```
   “installerUpdateArgs” : [“--quiet”, “--noWeb”], 

   “checkPendingReboot” :  “true” 
   ```

* **Actualización manual del paquete de actualizaciones de administrador en SCCM**: los parámetros de la línea de comandos de un paquete de actualización de administrador individual en SCCM también se pueden modificar de forma manual.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>Comprobación, informes y solución de códigos de error

### <a name="determining-that-visual-studio-was-updated"></a>Determinación de que se actualizó Visual Studio

Puede usar uno de los métodos siguientes para comprobar que la actualización de administrador se instaló correctamente: 

* En el equipo cliente, inicie Visual Studio 2019, seleccione **Ayuda**  > **Acerca de** y compruebe que el número de versión coincide con el último número del título de la actualización deseada. 

* Use la herramienta **vswhere** en el equipo cliente para identificar las distintas versiones de Visual Studio en el equipo. Para obtener más información, vea [Herramientas para detectar y administrar instancias de Visual Studio](../install/tools-for-managing-visual-studio-instances.md). 

* Cada intento de actualización administrativa genera varios archivos de registro en el directorio `%temp%` del equipo cliente que captura el progreso de la operación de actualización.Ordene la carpeta por fecha y busque los archivos que comienzan por `dd_updatedriver`, `dd_bootstrapper`, `dd_client` y  `dd_setup`  para las actualizaciones administrativas, el programa previo, el instalador de Visual Studio y el motor de instalación, respectivamente.Compruebe que estos archivos de registro contienen un 0, que indica que la actualización se aplicó correctamente. Tenga en cuenta que estos archivos de registro también se pueden utilizar para comprobar que se está usando el archivo de configuración. Consulte la [herramienta de recopilación de registros de Visual Studio](https://www.microsoft.com/download/details.aspx?id=12493) para obtener más detalles.     

### <a name="error-codes-and-conditions"></a>Códigos de error y condiciones

>[!IMPORTANT]
> Recuerde que Visual Studio debe cerrarse antes de instalar la actualización. Si Visual Studio está abierto o en uso, se cancelará la instalación de la actualización.

Es posible que las actualizaciones administrativas devuelvan los siguientes códigos de retorno:  

| Código de error | Definición |
|--|:-|
| 0 | La actualización administrativa se instaló correctamente. |
| 1001 | Se está ejecutando el instalador de Visual Studio o un proceso de instalación relacionado. La actualización no se ha aplicado. |
| 1002 | El instalador de Visual Studio está en pausa. La actualización no se ha aplicado. |
| 1003 | Visual Studio se está ejecutando. La actualización no se ha aplicado. Esta condición se puede anular mediante la marca `--force`. |
| 1004 | No se detectó Internet.La actualización no pudo ponerse en contacto con la ubicación de Internet que contiene los archivos actualizados. La actualización no se ha aplicado. |
| 1005 | El valor del Registro  **AdministratorUpdatesEnabled** está establecido en **0** o no está establecido. La actualización no se ha aplicado. |
| 1006 | El valor del Registro  **AdministratorUpdatesOptOut**  está establecido en **1**. La actualización no se ha aplicado. La clave está pensada para equipos cliente que no deben ser actualizados por el administrador. |
| 1007 | El instalador de Visual Studio no está instalado. |
| 1008 | El valor del registro **BaselineStickinessVersions2019** no se encuentra en un formato legible. El valor del Registro debe incluir **todas** las versiones o las versiones válidas con el número de compilación establecido en 0 explícitamente, por ejemplo, X.Y.0. |
| 3010 | El sistema requiere un reinicio. La actualización puede haberse aplicado o no. Reinicie el equipo e intente la actualización de nuevo. |
| Otros | Error al intentar aplicar la actualización.La actualización no se ha aplicado. |

Para obtener una lista exhaustiva de los códigos de error de cliente, consulte [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md). 

## <a name="feedback-and-support"></a>Comentarios y soporte técnico
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Puede usar los métodos siguientes para proporcionar comentarios acerca de las actualizaciones de administrador de Visual Studio o notificar problemas que afecten a las actualizaciones:
* Consulte las orientaciones de [Solución de problemas de instalación y actualización de Visual Studio](../install/troubleshooting-installation-issues.md).
* Formule preguntas a la comunidad en el [Foro de preguntas y respuestas de instalación de Visual Studio](https://docs.microsoft.com/answers/topics/vs-setup.html).
* Vaya a la [página de soporte técnico de Visual Studio](https://visualstudio.microsoft.com/vs/support/) y compruebe si el problema aparece en las preguntas más frecuentes.  También puede seleccionar el botón del [vínculo de soporte técnico](https://visualstudio.microsoft.com/vs/support/#talktous) para obtener ayuda por chat.
* [Proporcione comentarios sobre las características o notifique un problema](https://aka.ms/vs/wsus/feedback) al equipo de Visual Studio con respecto a esta experiencia de aplicación de actualizaciones de administrador.
* Póngase en contacto con el responsable técnico de cuentas de su organización para Microsoft.

## <a name="see-also"></a>Consulte también
* [Habilitación de las actualizaciones de administrador](../install/enabling-administrator-updates.md)    
* [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md)
* [Ciclo de vida y mantenimiento del producto de Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Notas de la versión de Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Notas de la versión de Visual Studio 2017](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [Instalación de Visual Studio](../install/install-visual-studio.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Herramientas para detectar y administrar instancias de Visual Studio](../install/tools-for-managing-visual-studio-instances.md)
* [Creación de una instalación de red de Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Definición de la configuración en un archivo de respuesta](../install/automated-installation-with-response-file.md)
* [Control updates to network-based Visual Studio deployments](../install/controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones de implementaciones de Visual Studio basadas en red)
* [Preguntas más frecuentes del catálogo de Microsoft Update](https://www.catalog.update.microsoft.com/faq.aspx)
* [Documentación de Microsoft Endpoint Configuration Manager (SCCM)](https://docs.microsoft.com/mem/configmgr)
* [Importación de actualizaciones desde el catálogo de Microsoft Update](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Documentación de Windows Server Update Services (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
