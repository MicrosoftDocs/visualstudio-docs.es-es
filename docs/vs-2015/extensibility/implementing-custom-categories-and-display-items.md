---
title: Implementación de las categorías personalizadas y mostrar los elementos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f84d66a1dc51baffe743b1f7c16b4bf0ff15ef3a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117907"
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementación de las categorías personalizadas y mostrar los elementos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un VSPackage puede proporcionar control de las fuentes y colores de su texto para el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE) a través de las categorías personalizadas y mostrar los elementos.  
  
 Categorías personalizadas y mostrar los elementos se encuentran en el **fuentes y colores** página de propiedades. Para abrir el **fuentes y colores** página de propiedades, en el **herramientas** menú, haga clic en **opciones**. Expanda **entorno** y, a continuación, haga clic en **fuentes y colores**.  
  
 Cuando se utiliza este mecanismo, los paquetes VSPackage deben implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaz y sus interfaces asociadas.  
  
 En principio, este mecanismo puede usarse para modificar todo lo existente **mostrar elementos** y **categorías** que contienen. Sin embargo, no debe utilizarse para modificar el **texto EditorCategory** o su **mostrar elementos**. Para obtener más información, consulte [información general de Color y fuente](../extensibility/font-and-color-overview.md).  
  
 Para implementar personalizado **categorías** o **mostrar elementos**, un VSPackage debe:  
  
- Cree o identifique categorías en el registro.  
  
   Implementación del IDE de la **fuentes y colores** página de propiedades usa esta información para consultar correctamente para el servicio que admite una categoría determinada.  
  
- Cree o identifique los grupos (opcionales) en el registro.  
  
   Puede ser útil definir un grupo, que representa la unión de dos o más categorías. Si se define un grupo, el IDE automáticamente combina las subcategorías y distribuye mostrar los elementos dentro del grupo.  
  
- Implementar la compatibilidad con IDE.  
  
- Controlar los cambios de fuente y color.  
  
  Para obtener información, consulte [acceso a fuente de almacenados y la configuración de Color](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Para crear o identificar categorías  
  
- Construir un tipo especial de entrada de registro de la categoría bajo [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<versión de Visual Studio >* \FontAndColors\\`<Category>`]  
  
   *\<Categoría >* es el nombre no traducido de la categoría.  
  
- Llenar el registro con dos valores:  
  
  |Name|Tipo|Datos|Descripción|  
  |----------|----------|----------|-----------------|  
  |Categoría|REG_SZ|GUID|Crea un GUID para identificar la categoría.|  
  |Paquete|REG_SZ|GUID|El GUID del servicio de VSPackage que admite la categoría.|  
  
  El servicio especificado en el registro debe proporcionar una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> para la categoría correspondiente.  
  
## <a name="to-create-or-identify-groups"></a>Para crear o identificar grupos  
  
- Construir un tipo especial de entrada de registro de la categoría bajo [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<versión de Visual Studio >* \FontAndColors\\  *\<grupo >*]  
  
   *\<grupo >* es el nombre no traducido del grupo.  
  
- Llenar el registro con dos valores:  
  
  |Name|Tipo|Datos|Descripción|  
  |----------|----------|----------|-----------------|  
  |Categoría|REG_SZ|GUID|Crea un GUID para identificar el grupo.|  
  |Paquete|REG_SZ|GUID|El GUID del servicio que admite la categoría.|  
  
  El servicio especificado en el registro debe proporcionar una implementación de `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` para el grupo correspondiente.  
  
## <a name="to-implement-ide-support"></a>Para implementar la compatibilidad con IDE  
  
- Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, que devuelve un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaz o un `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaz para el IDE para cada **categoría** o grupo GUID proporcionado.  
  
- Para cada **categoría** lo admite, un VSPackage implementa una instancia independiente de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaz.  
  
- Los métodos se implementan a través de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> debe proporcionar el IDE con:  
  
  - Listas de **mostrar elementos** en el **categoría.**  
  
  - Nombres localizables para **mostrar elementos**.  
  
  - Mostrar la información de cada miembro de **categoría**.  
  
  > [!NOTE]
  >  Cada **categoría** debe contener al menos un **Mostrar artículo**.  
  
- El IDE usa la `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaz para definir una unión de varias categorías.  
  
   Su implementación proporciona el IDE con:  
  
  - Una lista de los **categorías** que componen un grupo determinado.  
  
  - Acceso a las instancias de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> que admiten cada **categoría** dentro del grupo.  
  
  - Nombres de grupo localizable.  
  
- Actualizando el IDE:  
  
   El IDE se almacena en caché información acerca de **fuente y Color** configuración. Por lo tanto, después de cualquier modificación del IDE **fuente y Color** configuración, es aconsejable asegurarse de que la memoria caché está actualizada.  
  
  Actualizando la memoria caché se realiza a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz y se pueden realizados elementos seleccionados globalmente o solo en.  
  
## <a name="to-handle-font-and-color-changes"></a>Para controlar la fuente y Color cambia  
 Para admitir correctamente la coloración de texto que muestra un paquete VSPackage, el servicio de coloración compatible con el paquete VSPackage debe responder a los cambios iniciados por el usuario a través de la **fuentes y colores** página de propiedades. Un VSPackage para ello:  
  
- Controlar eventos generados por el IDE implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfaz.  
  
     El IDE llama al método apropiado siguiendo las modificaciones de usuario de la **fuentes y colores** página. Por ejemplo, llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> método si se selecciona una nueva fuente.  
  
     -o bien-  
  
- Sondear el IDE para que los cambios.  
  
     Esto puede hacerse a través del sistema implementado <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz. Aunque principalmente por compatibilidad con la persistencia, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> método puede utilizarse para obtener información de fuente y color para **mostrar elementos**. Para obtener más información, consulte [acceso a fuente de almacenados y la configuración de Color](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    >  Para asegurarse de que los resultados obtenidos mediante sondeo son correctos, puede ser útil usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz para determinar si se necesitan un vaciado de la caché y la actualización antes de llamar a los métodos de recuperación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Obtención de información de fuente y Color para la coloración de texto](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Obtener acceso a la configuración de Color y fuente almacenado](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Cómo: Obtener acceso a la combinación de colores y fuentes integradas](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Información general sobre fuentes y colores](../extensibility/font-and-color-overview.md)
