---
title: Compatibilidad con la configuración de usuario | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ece6ecc2d7a1a49d77643e18beced76403c13cc5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428780"
---
# <a name="support-for-user-settings"></a>Compatibilidad con la configuración de usuario
Un VSPackage puede definir uno o más categorías de configuración, que son grupos de variables de estado que se conservan cuando un usuario elige el **importar y exportar configuraciones** comando el **herramientas** menú. Para habilitar esta persistencia, se usa las API de configuración en el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

 Una entrada del registro que se conoce como un punto de configuración personalizado y un GUID que define la categoría de configuración de un VSPackage. Un VSPackage puede admitir varias categorías de configuración, cada uno definido por un punto de configuración personalizado.

- Las implementaciones de configuración que se basa en los ensamblados de interoperabilidad (mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interfaz) debe crear un punto de configuración personalizado mediante la edición del registro o mediante un script de registrador (archivo .rgs). Para obtener más información, consulta [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Código que utiliza Managed Package Framework (MPF) debe crear puntos de valores personalizados adjuntando un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> a VSPackage para cada punto de configuración personalizado.

     Si un VSPackage solo es compatible con varios puntos de valores personalizados, cada punto de configuración personalizado se implementa mediante una clase independiente y cada uno está registrado mediante una instancia única de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> clase. Por lo tanto, una configuración de implementación de clase puede admitir más de una categoría de configuración.

## <a name="custom-settings-point-registry-entry-details"></a>Detalles de la entrada de configuración personalizada del registro de punto
 Puntos de valores personalizados se crean en una entrada del registro en la siguiente ubicación: HKLM\Software\Microsoft\VisualStudio\\*\<versión >* \UserSettings\\`<CSPName>`, donde `<CSPName>` es el nombre del punto de configuración personalizado admita el VSPackage y  *\<versión >* es la versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], por ejemplo 8.0.

> [!NOTE]
> La ruta de acceso raíz de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versión >* puede reemplazarse por una alternativa raíz cuando el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es el entorno de desarrollo integrado (IDE) inicializar. Para obtener más información, consulte [modificadores de línea de comandos](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Se muestra la estructura de la entrada del registro:

 HKLM\Software\Microsoft\VisualStudio\\*\<Version>* \UserSettings\

 `<CSPName`>= s '#12345'

 Paquete = '{XXXX XXXXXX XXXX XXXX XXXXXXXXX}'

 Categoría = '{aaaa AAAAAA aaaa aaaa YYYYYYYYY}'

 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'

 AlternateParent = CategoryName

| Name | Tipo | Datos | Descripción |
|-----------------|--------| - | - |
| (Predeterminado) | REG_SZ | Nombre del punto de configuración personalizada | Nombre de la clave, `<CSPName`>, es el nombre no traducido del punto de configuración personalizada.<br /><br /> Para implementaciones basadas en MPF, nombre de la clave se obtiene mediante la combinación del `categoryName` y `objectName` argumentos de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructor en `categoryName_objectName`.<br /><br /> La clave puede estar vacía o puede contener el identificador de referencia a la cadena localizada en un archivo DLL satélite. Este valor se obtiene de la `objectNameResourceID` argumento para el <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructor. |
| Paquete | REG_SZ | GUID | El GUID del VSPackage que implemente el punto de configuración personalizado.<br /><br /> Las implementaciones en función de MPF usando el <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> clase, use el constructor `objectType` argumento que contiene el VSPackage <xref:System.Type> y reflexión para obtener este valor. |
| Categoría | REG_SZ | GUID | GUID que identifica la categoría de configuración.<br /><br /> Para implementaciones basadas en ensamblados de interoperabilidad, este valor puede ser un elegido arbitrariamente GUID, que el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pasa a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> métodos. Todas las implementaciones de estos dos métodos deben comprobar sus argumentos GUID.<br /><br /> Para implementaciones basadas en MPF, este GUID se obtiene mediante la <xref:System.Type> de la clase que implementa el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismo de configuración. |
| ResourcePackage | REG_SZ | GUID | Opcional.<br /><br /> Ruta de acceso a satélite DLL que contiene cadenas traducidas si la implementación de VSPackage no los proporciona.<br /><br /> MPF usa la reflexión para obtener el recurso correcto de VSPackage, por lo que la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> clase no establece este argumento. |
| AlternateParent | REG_SZ | Nombre de la carpeta en la página de opciones de herramientas que contiene este punto de configuración personalizado. | Opcional.<br /><br /> Debe establecer este valor solo si una implementación de configuración admite **herramientas-opciones** las páginas que usan el mecanismo de persistencia en el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] en lugar del mecanismo del modelo de automatización para guardar el estado.<br /><br /> En estos casos, el valor de la clave AlternateParent es el `topic` sección de la `topic.sub-topic` cadena usada para identificar la instancia concreta **ToolsOptions** página. Por ejemplo, para el **ToolsOptions** página `"TextEditor.Basic"` sería el valor de AlternateParent `"TextEditor"`.<br /><br /> Cuando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> genera el punto de configuración personalizado, es el mismo que el nombre de categoría. |
