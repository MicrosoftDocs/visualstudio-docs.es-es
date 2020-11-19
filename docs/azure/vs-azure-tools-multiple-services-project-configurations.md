---
title: Configurar el servicio en la nube con varias configuraciones
description: Cambie los archivos ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg y ServiceConfiguration.Cloud.cscfg para saber cómo configurar un proyecto de servicio en la nube de Azure.
ms.custom: SEO-VS-2020
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 58d7a967c3a8cf46330c169db1b73bc048a2110c
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902368"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Configuración de su proyecto de Azure en Visual Studio para usar varias configuraciones de servicio

Un proyecto de servicio en la nube de Azure en Visual Studio incluye tres archivos de configuración: `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg` y `ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` se implementa en Azure para describir los requisitos del servicio en la nube y sus roles y para proporcionar la configuración que se aplica a todas las instancias. La configuración se puede leer en tiempo de ejecución mediante la API de tiempo de ejecución de hospedaje del servicio de Azure. Este archivo puede actualizarse en Azure solo cuando se detiene el servicio en la nube.
- `ServiceConfiguration.Local.cscfg` y `ServiceConfiguration.Cloud.cscfg` proporcionan valores de configuración del archivo de definición y especifican el número de instancias que se van a ejecutar en cada rol. El archivo "Local" contiene valores que se utilizan en la depuración local; el archivo "Nube" se implementa en Azure como `ServiceConfiguration.cscfg` y proporciona la configuración para el entorno de servidor. Este archivo se puede actualizar mientras el servicio en la nube se ejecuta en Azure.

Las opciones de configuración se administran y modifican en Visual Studio con las páginas de propiedades del rol aplicable (haga clic con el botón derecho en el rol y seleccione **Propiedades**, o bien haga doble clic en el rol). Los cambios pueden limitarse a cualquier configuración elegida en el menú desplegable **Configuración de servicio**. Las propiedades de los roles de web y de trabajo son similares, excepto en los casos descritos en las siguientes secciones.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Para obtener información acerca de los esquemas subyacentes para los archivos de configuración y definición de servicio, vea los artículos [Esquema XML de .csdef](/azure/cloud-services/schema-csdef-file) y [Esquema XML de .csdef](/azure/cloud-services/schema-cscfg-file). Para obtener más información sobre la configuración del servicio, consulte [Configuración de Cloud Services](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Página Configuración

### <a name="service-configuration"></a>Configuración de servicio

Seleccione a qué archivo `ServiceConfiguration.*.cscfg` afectan los cambios. De forma predeterminada, están las variantes Local y Nube, y puede usar el comando **Administrar...** para copiar y eliminar archivos de configuración y cambiarles el nombre. Estos archivos se agregan a su proyecto de servicio en la nube y aparecen en el **Explorador de soluciones**. Sin embargo, el cambio de nombre o la eliminación de la configuración solo se puede realizar con este control.

### <a name="instances"></a>Instancias

Establezca la propiedad **Número de instancias** en el número de instancias que el servicio debe ejecutar para este rol

Establezca la propiedad **Tamaño de VM** en **Extra pequeño**, **Pequeño**, **Mediano**, **Grande** o **Extra grande**.  Para obtener más información, vea [tamaños de Cloud Services](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Acción de inicio (solo para el rol web)

Establezca esta propiedad para especificar que Visual Studio debería iniciar un explorador web para los extremos HTTP, los extremos HTTPS o ambos al iniciar la depuración.

La opción de **extremo https** solo está disponible si ya ha definido un punto de conexión HTTPS para el rol. Puede definir un extremo HTTPS en la página de propiedades **Extremos** .

Si ya se ha agregado un extremo HTTPS, la opción de extremo HTTPS se habilita de forma predeterminada, y Visual Studio iniciará un explorador para este extremo al comenzar la depuración, además de a un explorador para el extremo HTTP, pero se asume que ambas opciones de inicio están habilitadas.

### <a name="diagnostics"></a>Diagnóstico

De manera predeterminada, la funcionalidad de diagnóstico está habilitada para el rol web. El proyecto de servicio en la nube de Azure y la cuenta de almacenamiento se establecen para usar el emulador de almacenamiento local. Cuando esté listo para realizar la implementación en Azure, puede seleccionar el botón del generador (**…**) para usar Azure Storage en su lugar. Los datos de diagnóstico se pueden transferir a la cuenta de almacenamiento a petición o a intervalos programados automáticamente. Para obtener más información sobre los diagnósticos de Azure, consulte [Habilitación de Diagnósticos en Azure Cloud Services y Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Página de configuración

En la página **Configuración**, puede agregar la configuración como pares nombre-valor. El código que se ejecuta en el rol puede leer los valores de las opciones de configuración en tiempo de ejecución mediante las clases proporcionadas por la [biblioteca administrada de Azure](/previous-versions/azure/dn602775(v=azure.11)), en concreto, el método [GetConfigurationSettingValue](/previous-versions/azure/reference/ee772857(v=azure.100)) .

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Configuración de una cadena de conexión para una cuenta de almacenamiento

Una cadena de conexión es un valor de configuración que proporciona información de conexión y autenticación para el emulador de almacenamiento o para una cuenta de Azure Storage. Cada vez que el código de un rol accede a Azure Storage (blobs, colas o tablas), necesita una cadena de conexión.

> [!Note]
> Una cadena de conexión de una cuenta de Azure Storage debe usar un formato definido (vea [Configuración de las cadenas de conexión de Azure Storage](/azure/storage/common/storage-configure-connection-string)).

Puede establecer la cadena de conexión para usar el almacenamiento local según sea necesario y, después, definirla en una cuenta de Azure Storage al implementar la aplicación en el servicio en la nube. Si la cadena de conexión no se configura correctamente, puede que el rol no se inicie o que pase por los estados de inicialización, ocupado y detenido.

Para crear una cadena de conexión, seleccione **Agregar configuración** y establezca el **Tipo** en "Cadena de conexión".

En el caso de las cadenas de conexión nuevas o existentes, seleccione **...** _ a la derecha del campo _ *Value** para abrir el cuadro de diálogo **crear cadena de conexión de almacenamiento** :

1. En **Conectar mediante**, elija la opción **Su suscripción** para seleccionar una cuenta de almacenamiento de una suscripción. Después, Visual Studio obtiene las credenciales de la cuenta de almacenamiento automáticamente del archivo `.publishsettings`.
1. Si selecciona **Credenciales escritas manualmente**, puede especificar el nombre de la cuenta y la clave directamente con la información de Azure Portal. Para copiar la clave de cuenta:
    1. Vaya a la cuenta de almacenamiento en Azure Portal y seleccione **Administrar claves**.
    1. Para copiar la clave de cuenta, vaya a la cuenta de almacenamiento en Azure Portal, seleccione **Configuración > Claves de acceso** y use el botón Copiar para copiar la clave de acceso principal en el Portapapeles.
1. Seleccione una de las opciones de conexión. En **Especificar extremos personalizados** se le pide que especifique direcciones URL específicas para los blobs, las tablas y las colas. Los puntos de conexión personalizados permiten usar [dominios personalizados](/azure/storage/blobs/storage-custom-domain-name) y controlar el acceso con mayor precisión. Consulte [Configuración de las cadenas de conexión de Azure Storage](/azure/storage/common/storage-configure-connection-string).
1. Seleccione **Aceptar** y, después, **Archivo > Guardar**, para actualizar la configuración con la nueva cadena de conexión.

Una vez más, al publicar su aplicación en Azure, elija la configuración del servicio que contiene la cuenta de Azure Storage para la cadena de conexión. Una vez publicada la aplicación, compruebe que funciona según lo previsto con los servicios de almacenamiento de Azure.

Para más información acerca de cómo actualizar configuraciones del servicio, vea la sección [Administrar cadenas de conexión para cuentas de almacenamiento](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Página Extremos

Un rol web suele tener un único punto de conexión HTTP en el puerto 80. En cambio, un rol de trabajo puede tener cualquier número de puntos de conexión HTTP, HTTPS o TCP. Los extremos pueden ser extremos de entrada (que están disponibles para los clientes externos) o extremos internos (que están disponibles para otros roles que se ejecuten dentro del servicio).

- Para hacer que un extremo HTTP esté disponible para clientes externos y exploradores web, cambie el tipo del extremo para que sea de entrada, y especifique un nombre y un número de puerto público.
- Para hacer que un extremo HTTPS esté disponible para clientes externos y exploradores web, cambie el tipo del extremo para que sea de **entrada**, y especifique un nombre, un número de puerto público y un nombre de certificado de administración. También debe definir el certificado en la página de propiedades **Certificados** para poder especificar un certificado de administración.
- Para hacer que un extremo esté disponible para el acceso interno de otros roles del servicio en la nube, cambie el tipo del extremo para que sea interno, y especifique un nombre y los puertos privados posibles para el extremo.

## <a name="local-storage-page"></a>Pagina Almacenamiento local

Puede usar la página de propiedades **Almacenamiento local** para reservar uno o más recursos de almacenamiento local para un rol. Un recurso de almacenamiento local es un directorio reservado en el sistema de archivos de la máquina virtual de Azure donde se ejecuta una instancia de un rol.

## <a name="certificates-page"></a>Página Certificados

La página de propiedades **Certificados** agrega información sobre los certificados a la configuración del servicio. Tenga en cuenta que sus certificados no se incluyen con el servicio, debe cargarlos por separado en Azure mediante [Azure Portal](https://portal.azure.com).

Si incorpora un certificado aquí, se agrega información sobre los certificados a la configuración del servicio. Los certificados no se incluyen con el servicio; debe cargarlos por separado mediante Azure Portal.

Para asociar un certificado a su rol, proporcione un nombre para el certificado. Use este nombre para hacer referencia al certificado cuando configure un punto de conexión HTTPS en la página **Puntos de conexión**. A continuación, especifique si el almacén de certificados es **Equipo local** o **Usuario actual**, así como el nombre del almacén. Por último, especifique la huella digital del certificado. Si el certificado está en el almacén Current User\Personal (My), para especificar la huella digital del certificado selecciónelo en una lista rellenada. Si se encuentra en otra ubicación, especifique el valor de la huella digital manualmente.

Al agregar un certificado del almacén de certificados, cualquier certificado intermedio se agrega automáticamente a la configuración. Además, estos certificados intermedios deben cargarse en Azure para configurar el servicio correctamente para SSL.

Cualquier certificado de administración que asocie a su servicio solo se aplicará a su servicio cuando se ejecute en la nube. Cuando el servicio se ejecuta en el entorno de desarrollo local, usa un certificado estándar administrado por el emulador de proceso.
