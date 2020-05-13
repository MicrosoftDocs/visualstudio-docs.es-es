---
title: Soporte para la configuración de usuario ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704787"
---
# <a name="support-for-user-settings"></a>Compatibilidad con la configuración de usuario
Un VSPackage puede definir una o varias categorías de configuración, que son grupos de variables de estado que persisten cuando un usuario elige el comando **Importar/Exportar configuración** en el menú **Herramientas.** Para habilitar esta persistencia, utilice las [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]API de configuración en el archivo .

 Una entrada del Registro que se conoce como un punto de configuración personalizado y un GUID define la categoría de configuración de un VSPackage. Un VSPackage puede admitir varias categorías de configuración, cada una definida por un punto de configuración personalizado.

- Las implementaciones de la configuración basada en <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> ensamblados de interoperabilidad (mediante la interfaz) deben crear un punto de configuración personalizado editando el registro o utilizando un script de registrador (archivo .rgs). Para obtener más información, consulta [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- El código que usa Managed Package Framework (MPF) debe <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> crear puntos de configuración personalizados adjuntando un al VSPackage para cada punto de configuración personalizado.

     Si un único VSPackage admite varios puntos de configuración personalizados, cada punto de configuración personalizado <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> se implementa mediante una clase independiente y cada uno está registrado por una instancia única de la clase. Por lo tanto, una configuración que implementa la clase puede admitir más de una categoría de configuración.

## <a name="custom-settings-point-registry-entry-details"></a>Detalles de la entrada del registro de puntos de configuración personalizada
 Los puntos de configuración personalizados se crean en una entrada del\\Registro en\\`<CSPName>`la `<CSPName>` siguiente ubicación: HKLM, Software, Microsoft, VisualStudio*\<Versión>*, donde está el nombre del punto de configuración personalizado que admite VSPackage y * \<Version>* es la versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], por ejemplo, 8.0.

> [!NOTE]
> La ruta de acceso de la\\raíz de HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VisualStudio*\<Versión>* se puede invalidar con una raíz alternativa cuando se inicializa el entorno de desarrollo integrado (IDE). Para obtener más información, consulte [Conmutadores de línea de comandos](../../extensibility/command-line-switches-visual-studio-sdk.md).

 La estructura de la entrada del registro se ilustra a continuación:

 HKLM, Software, Microsoft,\\VisualStudio*\<Versión>* de Usuario.

 `<CSPName`>'#12345'

 Paquete á ''XXXXXX XXXX XXXX XXXXXXXXX''

 Categoría ''YYYYYA AAAA AAAA AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

 Paquete de Recursos de la Imagen zzzzZZZZZZZZZzZz ZZZZZZZZZ'

 AlternateParent - CategoryName

| Nombre | Tipo | data | Descripción |
|-----------------|--------| - | - |
| (Es el valor predeterminado). | REG_SZ | Nombre del punto de configuración personalizado | El nombre de `<CSPName` la clave,>, es el nombre no localizado del punto de configuración personalizado.<br /><br /> Para las implementaciones basadas en MPF, el nombre `categoryName` `objectName` de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> clave `categoryName_objectName`se obtiene combinando los argumentos y del constructor en .<br /><br /> La clave puede estar vacía o puede contener el identificador de referencia de la cadena localizada en un archivo DLL satélite. Este valor se obtiene `objectNameResourceID` del <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> argumento al constructor. |
| Paquete | REG_SZ | GUID | Guid del VSPackage que implementa el punto de configuración personalizado.<br /><br /> Implementaciones basadas en <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> MPF mediante la `objectType` clase, use el <xref:System.Type> argumento del constructor que contiene el VSPackage y la reflexión para obtener este valor. |
| Category | REG_SZ | GUID | GUID que identifica la categoría de configuración.<br /><br /> Para las implementaciones basadas en ensamblados de interoperabilidad, este [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] valor puede ser <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> GUID elegido arbitrariamente, que el IDE pasa a los métodos y. Todas las implementaciones de estos dos métodos deben comprobar sus argumentos GUID.<br /><br /> Para las implementaciones basadas en MPF, <xref:System.Type> este GUID [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se obtiene mediante la de la clase que implementa el mecanismo de configuración. |
| ResourcePackage | REG_SZ | GUID | Opcional.<br /><br /> Ruta de acceso a DLL satélite que contiene cadenas localizadas si el VSPackage de implementación no las proporciona.<br /><br /> MPF usa la reflexión para obtener el <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> recurso correcto VSPackage, por lo que la clase no establece este argumento. |
| AlternateParent | REG_SZ | Nombre de la carpeta en la página Opciones de herramientas que contiene este punto de configuración personalizado. | Opcional.<br /><br /> Debe establecer este valor solo si **Tools Options** una implementación de configuración admite [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] páginas de opciones de herramientas que usan el mecanismo de persistencia en el mecanismo en lugar del mecanismo en lugar del modelo de automatización para guardar el estado.<br /><br /> En estos casos, el valor de `topic` la clave `topic.sub-topic` AlternateParent es la sección de la cadena utilizada para identificar la página **ToolsOptions** determinada. Por ejemplo, para la `"TextEditor.Basic"` página **ToolsOptions** el `"TextEditor"`valor de AlternateParent sería .<br /><br /> Cuando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> se genera el punto de configuración personalizado, es el mismo que el nombre de la categoría. |
