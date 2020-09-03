---
title: Compatibilidad con la configuración de usuario | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704787"
---
# <a name="support-for-user-settings"></a>Compatibilidad con la configuración de usuario
Un VSPackage puede definir una o varias categorías de configuración, que son grupos de variables de estado que se conservan cuando un usuario elige el comando **importar o exportar configuraciones** en el menú **herramientas** . Para habilitar esta persistencia, se usan las API de configuración de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 Una entrada del registro a la que se hace referencia como un punto de configuración personalizado y un GUID define la categoría de configuración de un VSPackage. Un VSPackage puede admitir varias categorías de configuración, cada una definida por un punto de configuración personalizado.

- Las implementaciones de valores que se basan en ensamblados de interoperabilidad (mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interfaz) deben crear un punto de configuración personalizado editando el registro o usando un script de registrador (archivo. RGS). Para obtener más información, consulta [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- El código que usa Managed Package Framework (MPF) debe crear puntos de configuración personalizados adjuntando un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> al VSPackage para cada punto de configuración personalizado.

     Si un único VSPackage admite varios puntos de configuración personalizados, cada punto de configuración personalizado se implementa mediante una clase independiente, y cada uno de ellos se registra mediante una instancia única de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> clase. Por consiguiente, una configuración que implementa la clase puede admitir más de una categoría de configuración.

## <a name="custom-settings-point-registry-entry-details"></a>Detalles de la entrada del registro de punto de configuración personalizada
 Los puntos de configuración personalizados se crean en una entrada del registro en la siguiente ubicación: HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings \\ `<CSPName>` , donde `<CSPName>` es el nombre del punto de configuración personalizado que el VSPackage admite y *\<Version>* es la versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , por ejemplo 8,0.

> [!NOTE]
> La ruta de acceso raíz de HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* se puede invalidar con una raíz alternativa cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se inicializa el entorno de desarrollo integrado (IDE). Para obtener más información, vea [modificadores de la línea de comandos](../../extensibility/command-line-switches-visual-studio-sdk.md).

 La estructura de la entrada del registro se ilustra a continuación:

 HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings\

 `<CSPName`>= s ' #12345 '

 Paquete = ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX} '

 Category = ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY} '

 ResourcePackage = ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ} '

 AlternateParent = NombreCategoría

| Nombre | Tipo | data | Descripción |
|-----------------|--------| - | - |
| (Es el valor predeterminado). | REG_SZ | Nombre del punto de configuración personalizado | El nombre de la clave, `<CSPName`>, es el nombre no traducido del punto de configuración personalizado.<br /><br /> Para las implementaciones basadas en MPF, el nombre de la clave se obtiene mediante la combinación `categoryName` `objectName` de los argumentos y del <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructor en `categoryName_objectName` .<br /><br /> La clave puede estar vacía o puede contener el ID. de referencia de la cadena traducida en un archivo DLL satélite. Este valor se obtiene del `objectNameResourceID` argumento en el <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructor. |
| Paquete | REG_SZ | GUID | GUID del VSPackage que implementa el punto de configuración personalizado.<br /><br /> Las implementaciones basadas en MPF mediante la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> clase, usan el argumento del constructor `objectType` que contiene el VSPackage <xref:System.Type> y la reflexión para obtener este valor. |
| Category | REG_SZ | GUID | GUID que identifica la categoría de configuración.<br /><br /> Para las implementaciones basadas en ensamblados de interoperabilidad, este valor puede ser un GUID elegido arbitrariamente, que el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pasa a los <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> métodos y. Todas las implementaciones de estos dos métodos deben comprobar sus argumentos GUID.<br /><br /> Para las implementaciones basadas en MPF, este GUID lo obtiene el <xref:System.Type> de la clase que implementa el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismo de configuración. |
| ResourcePackage | REG_SZ | GUID | Opcional.<br /><br /> Ruta de acceso al archivo DLL satélite que contiene cadenas traducidas si el VSPackage de implementación no las proporciona.<br /><br /> MPF utiliza la reflexión para obtener el VSPackage de recursos correcto, por lo que la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> clase no establece este argumento. |
| AlternateParent | REG_SZ | Nombre de la carpeta en la página Opciones de herramientas que contiene este punto de configuración personalizado. | Opcional.<br /><br /> Debe establecer este valor solo si una implementación de configuración admite páginas de **Opciones de herramientas** que usan el mecanismo de persistencia en [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , en lugar del mecanismo del modelo de automatización, para guardar el estado.<br /><br /> En estos casos, el valor de la clave AlternateParent es la `topic` sección de la `topic.sub-topic` cadena que se usa para identificar la página **ToolsOptions** determinada. Por ejemplo, para la página **ToolsOptions** , `"TextEditor.Basic"` el valor de AlternateParent sería `"TextEditor"` .<br /><br /> Cuando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> genera el punto de configuración personalizado, es el mismo que el nombre de categoría. |
