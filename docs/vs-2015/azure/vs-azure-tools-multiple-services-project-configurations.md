---
title: Configuración de su proyecto Azure mediante varias configuraciones de servicio | Microsoft Docs
description: Obtenga información sobre cómo configurar un proyecto de servicio de nube de Azure modificando los archivos ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg y ServiceConfiguration.Cloud.cscfg.
author: ghogen
manager: douge
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: f309c2a960d011601a9fdd41e29d767c667de838
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002935"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Configuración del proyecto de Azure en Visual Studio para usar varias configuraciones de servicio

Un proyecto de servicio de nube de Azure en Visual Studio incluye tres archivos de configuración: `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg`, y `ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` se implementa en Azure para describir los requisitos de servicio en la nube y sus roles y para proporcionar la configuración que se aplica a todas las instancias. Configuración se puede leer en tiempo de ejecución mediante la API de tiempo de ejecución de hospedaje de servicios de Azure. Este archivo puede actualizarse en Azure solo cuando se detiene el servicio en la nube.
- `ServiceConfiguration.Local.cscfg` y `ServiceConfiguration.Cloud.cscfg` proporcionan valores de configuración en la definición de archivo y especifique el número de instancias que se ejecuta para cada rol. El archivo "Local" contiene valores utilizados en la depuración local; el archivo "En la nube" se implementa en Azure como `ServiceConfiguration.cscfg` y proporciona la configuración para el entorno de servidor. Este archivo se puede actualizar mientras se está ejecutando el servicio de nube en Azure.

Opciones de configuración se administran y modifican en Visual Studio mediante las páginas de propiedades para el rol aplicable (haga clic en el rol y seleccione **propiedades**, o haga doble clic en el rol). Los cambios pueden limitarse a cualquier configuración elegida en el **configuración del servicio** lista desplegable. Las propiedades de los roles web y de trabajo son similares, excepto donde se describe en las secciones siguientes.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Para obtener información acerca de los esquemas subyacentes para los archivos de configuración y definición de servicio, vea el [esquema XML de .csdef](/azure/cloud-services/schema-csdef-file.md) y [esquema XML de .csdef](/azure/cloud-services/schema-cscfg-file.md) artículos. Para obtener más información acerca de la configuración del servicio, consulte [cómo configurar Cloud Services](/azure/cloud-services/cloud-services-how-to-configure-portal).


## <a name="configuration-page"></a>Página de configuración

### <a name="service-configuration"></a>Configuración del servicio

Seleccione a qué `ServiceConfiguration.*.cscfg` archivo se ve afectado por los cambios. De forma predeterminada, existen variantes Local y en la nube, y puede usar el **administrar...**  comando Copiar, cambiar el nombre y quitar archivos de configuración. Estos archivos se agregan al proyecto de servicio en la nube y aparecen en **el Explorador de soluciones**. Sin embargo, el cambio de nombre o quitar configuraciones puede realizarse solo desde este control.

### <a name="instances"></a>Instancias

Establecer el **instancia** count (propiedad) para el número de instancias que se debe ejecutar el servicio para este rol.

Establecer el **tamaño de máquina virtual** propiedad **Extra pequeño**, **pequeño**, **medio**, **grande**, o **Extragrande**.  Para obtener más información, consulte [tamaños de Cloud Services](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Acción de inicio (solo para el rol Web)

Establezca esta propiedad para especificar que Visual Studio debería iniciar un explorador web para los extremos HTTP o los puntos de conexión HTTPS o ambos al iniciar la depuración.

El **extremo HTTPS** opción solo está disponible si ya ha definido un extremo HTTPS para el rol. Puede definir un extremo HTTPS en el **extremos** página de propiedades.

Si ya ha agregado un extremo HTTPS, la opción de extremo HTTPS está habilitada de forma predeterminada, y Visual Studio inicia un explorador para este punto de conexión al iniciar la depuración, además de un explorador para el extremo HTTP, suponiendo que ambas opciones de inicio están habilitadas.

### <a name="diagnostics"></a>Diagnóstico

De forma predeterminada, se habilitan los diagnósticos para el rol Web. La cuenta de almacenamiento y el proyecto de servicio de nube de Azure se establecen para usar el emulador de almacenamiento local. Cuando esté listo para implementar en Azure, puede seleccionar el botón generador (**...** ) para usar Azure storage en su lugar. Puede transferir los datos de diagnóstico para la cuenta de almacenamiento a petición o en intervalos programados automáticamente. Para obtener más información sobre diagnósticos de Azure, consulte [habilitación de diagnósticos en Azure Cloud Services y Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Página de configuración

En el **configuración** página, puede agregar valores a una configuración como pares nombre / valor. Código que se ejecuta en el rol puede leer los valores de las opciones de configuración en tiempo de ejecución mediante las clases proporcionadas por el [biblioteca administrada de Azure](http://go.microsoft.com/fwlink?LinkID=171026), concretamente, el [GetConfigurationSettingValue](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.getconfigurationsettingvalue.aspx) método.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Configuración de una cadena de conexión para una cuenta de almacenamiento

Una cadena de conexión es un valor que proporciona información de conexión y autenticación para el emulador de almacenamiento o para una cuenta de almacenamiento de Azure. Cada vez que el código en un rol tiene acceso a Azure storage (blobs, colas o tablas), necesita una cadena de conexión.

> [!Note]
> Una cadena de conexión para la cuenta de Azure storage debe usar un formato definido (vea [configurar cadenas de conexión de Azure Storage](/azure/storage/common/storage-configure-connection-string)).

Puede establecer la cadena de conexión para usar el almacenamiento local según sea necesario y, a continuación, se establece en una cuenta de almacenamiento de Azure al implementar la aplicación de servicio en la nube. No se pudo establecer la cadena de conexión correctamente puede provocar que su rol no se inicie, o para desplazarse por los Estados inicializando, ocupados y deteniendo.

Para crear una cadena de conexión, seleccione **Agregar configuración** y establecer **tipo** a "Connection String".

Para las cadenas de conexión nueva o existente, seleccione **...** * a la derecha de la **valor** campo para abrir el **crear cadena de conexión de almacenamiento** cuadro de diálogo:

1. En **conectarse mediante**, elija el **su suscripción** opción para seleccionar una cuenta de almacenamiento de una suscripción. Visual Studio, a continuación, obtiene las credenciales de cuenta de almacenamiento automáticamente desde el `.publishsettings` archivo.
1. Seleccionar **credenciales escritas manualmente** le permite especificar el nombre de cuenta y clave directamente con la información desde el portal de Azure. Para copiar la clave de cuenta:
    1. Vaya a la cuenta de almacenamiento en Azure portal y seleccione **administrar claves**.
    1. Para copiar la clave de cuenta, vaya a la cuenta de almacenamiento en Azure portal, seleccione **configuración > claves de acceso**, a continuación, use el botón Copiar para copiar la clave de acceso principal en el Portapapeles.
1. Seleccione una de las opciones de conexión. **Especificar extremos personalizados** le pide que especifique las direcciones URL específicas para blobs, tablas y pone en cola. Puntos de conexión personalizados permiten usar [dominios personalizados](/azure/storage/blobs/storage-custom-domain-name.md) y para controlar el acceso más exactamente. Consulte [configurar cadenas de conexión de almacenamiento de Azure](/azure/storage/common/storage-configure-connection-string).
1. Seleccione **Aceptar**, a continuación, **archivo > Guardar** para actualizar la configuración con la nueva cadena de conexión.

De nuevo, al publicar su aplicación en Azure, elija la configuración del servicio que contiene la cuenta de almacenamiento de Azure para la cadena de conexión. Una vez publicada la aplicación, compruebe que la aplicación funciona según lo previsto con los servicios de almacenamiento de Azure.

Para obtener más información acerca de cómo actualizar configuraciones del servicio, vea la sección [administrar cadenas de conexión para las cuentas de almacenamiento](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Página extremos

Un rol web suele tener un único punto de conexión HTTP en el puerto 80. Por otro lado, un rol de trabajo, puede tener cualquier número de puntos de conexión HTTP, HTTPS o TCP. Los puntos de conexión pueden ser extremos de entrada, que están disponibles para los clientes externos, o puntos de conexión internos, que están disponibles para otros roles que se ejecutan en el servicio.

- Para que un extremo HTTP esté disponible para los clientes externos y exploradores Web, cambie el tipo de punto de conexión a la entrada y especifique un nombre y un número de puerto público.
- Para que un extremo HTTPS esté disponible para los clientes externos y exploradores Web, cambie el tipo de punto de conexión a **entrada**y especifique un nombre, un número de puerto público y un nombre de certificado de administración. También debe definir el certificado en el **certificados** página de propiedades para poder especificar un certificado de administración. 
- Para que un punto de conexión esté disponible para el acceso interno por otros roles de servicio en la nube, cambiar el tipo de punto de conexión internos y especifique un nombre y los puertos privados posibles para este extremo.

## <a name="local-storage-page"></a>Página de almacenamiento local

Puede usar el **almacenamiento Local** página de propiedades para reservar uno o varios recursos de almacenamiento local para un rol. Un recurso de almacenamiento local es un directorio reservado en el sistema de archivos de la máquina virtual de Azure en el que se está ejecutando una instancia de un rol.

## <a name="certificates-page"></a>Página certificados

El **certificados** página propiedad agrega información sobre los certificados para la configuración del servicio. Tenga en cuenta que los certificados no se empaquetan con su servicio. debe cargar sus certificados por separado en Azure a través de la [portal Azure](http://portal.azure.com).

Agregar un certificado aquí, agrega información sobre los certificados para la configuración del servicio. Los certificados no se empaquetan con el servicio. debe cargar sus certificados por separado mediante el portal de Azure.

Para asociar un certificado a un rol, proporcione un nombre para el certificado. Use este nombre para hacer referencia al certificado cuando configure un extremo HTTPS en el **extremos** página. A continuación, especifique si el almacén de certificados es **máquina Local** o **usuario actual** y el nombre de la tienda. Por último, especifique la huella digital del certificado. Si el certificado está en el Current User\Personal (My) almacén, puede especificar la huella digital del certificado, seleccione el certificado en una lista rellenada. Si se encuentra en cualquier otra ubicación, escriba el valor de huella digital manualmente.

Cuando se agrega un certificado del almacén de certificados, cualquier certificado intermedio se agrega automáticamente a los valores de configuración para usted. Además, estos certificados intermedios deben cargarse en Azure para configurar el servicio correctamente para SSL.

Cualquier certificado de administración que asocie a su servicio sólo se aplica a su servicio cuando se está ejecutando en la nube. Cuando el servicio se está ejecutando en el entorno de desarrollo local, usa un certificado estándar administrado por el emulador de proceso.
