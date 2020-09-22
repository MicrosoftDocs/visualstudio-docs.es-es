---
title: Implementar categorías personalizadas y mostrar elementos | Microsoft Docs
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
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842610"
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementación de categorías y elementos para mostrar personalizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un VSPackage puede proporcionar el control de las fuentes y los colores de su texto al [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE) a través de las categorías personalizadas y mostrar los elementos.  
  
 Las categorías personalizadas y los elementos para mostrar se encuentran en la página de propiedades **fuentes y colores** . Para abrir la página de propiedades **fuentes y colores** , en el menú **herramientas** , haga clic en **Opciones**. Expanda **entorno** y, a continuación, haga clic en **fuentes y colores**.  
  
 Al utilizar este mecanismo, los VSPackages deben implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaz y sus interfaces asociadas.  
  
 En principio, este mecanismo se puede usar para modificar todos los **elementos de presentación** existentes y las **categorías** que los contienen. Sin embargo, no debe usarse para modificar el **texto EditorCategory** o sus **elementos para mostrar**. Para obtener más información, vea [información general sobre fuentes y colores](../extensibility/font-and-color-overview.md).  
  
 Para implementar **categorías** personalizadas o **Mostrar los elementos**, un VSPackage debe:  
  
- Cree o identifique categorías en el registro.  
  
   La implementación del IDE de la página de propiedades **fuentes y colores** usa esta información para consultar correctamente el servicio que admite una categoría determinada.  
  
- Cree o identifique grupos (opcional) en el registro.  
  
   Puede ser útil definir un grupo, que representa la Unión de dos o más categorías. Si se define un grupo, el IDE combina automáticamente las subcategorías y distribuye los elementos que se muestran dentro del grupo.  
  
- Implementar la compatibilidad con el IDE.  
  
- Controlar los cambios de fuente y color.  
  
  Para obtener más información, vea [acceso a la configuración de fuente y color almacenados](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Para crear o identificar categorías  
  
- Construya un tipo especial de entrada de registro de categoría en [Hklm\software\microsoft. \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ `<Category>` ]  
  
   *\<Category>* es el nombre no traducido de la categoría.  
  
- Rellene el registro con dos valores:  
  
  |Nombre|Tipo|data|Descripción|  
  |----------|----------|----------|-----------------|  
  |Category|REG_SZ|GUID|GUID creado para identificar la categoría.|  
  |Paquete|REG_SZ|GUID|GUID del servicio VSPackage que admite la categoría.|  
  
  El servicio especificado en el registro debe proporcionar una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> para la categoría correspondiente.  
  
## <a name="to-create-or-identify-groups"></a>Para crear o identificar grupos  
  
- Construya un tipo especial de entrada de registro de categoría en [Hklm\software\microsoft. \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<group>* ]  
  
   *\<group>* es el nombre no traducido del grupo.  
  
- Rellene el registro con dos valores:  
  
  |Nombre|Tipo|data|Descripción|  
  |----------|----------|----------|-----------------|  
  |Category|REG_SZ|GUID|GUID creado para identificar el grupo.|  
  |Paquete|REG_SZ|GUID|GUID del servicio que admite la categoría.|  
  
  El servicio especificado en el registro debe proporcionar una implementación de `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` para el grupo correspondiente.  
  
## <a name="to-implement-ide-support"></a>Para implementar la compatibilidad con IDE  
  
- Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A> , que devuelve una <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaz o una `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaz al IDE para cada **categoría** o GUID de grupo proporcionado.  
  
- Para cada **categoría** que admite, un VSPackage implementa una instancia independiente de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaz.  
  
- Los métodos implementados mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> deben proporcionar el IDE con:  
  
  - Listas de **Mostrar los elementos** de la **categoría.**  
  
  - Nombres localizables para **Mostrar los elementos**.  
  
  - Mostrar información para cada miembro de la **categoría**.  
  
  > [!NOTE]
  > Cada **categoría** debe contener al menos un **elemento de presentación**.  
  
- El IDE usa la `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaz para definir una Unión de varias categorías.  
  
   Su implementación proporciona el IDE con:  
  
  - Una lista de las **categorías** que componen un grupo determinado.  
  
  - Acceso a las instancias de que <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> admiten cada **categoría** dentro del grupo.  
  
  - Nombres de grupo localizables.  
  
- Actualización del IDE:  
  
   El IDE almacena en caché información acerca de la configuración de **fuente y color** . Por lo tanto, después de modificar la configuración de **fuente y color** del IDE, es aconsejable asegurarse de que la memoria caché esté actualizada.  
  
  La actualización de la memoria caché se realiza a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz y puede realizarse globalmente o solo en los elementos seleccionados.  
  
## <a name="to-handle-font-and-color-changes"></a>Para controlar los cambios de fuente y color  
 Para admitir correctamente la coloración del texto que muestra un VSPackage, el servicio de coloración que admite el VSPackage debe responder a los cambios iniciados por el usuario realizados a través de la página de propiedades **fuentes y colores** . Para ello, un VSPackage hace lo siguiente:  
  
- Controlar los eventos generados por el IDE implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfaz.  
  
     El IDE llama al método adecuado después de las modificaciones del usuario de la página **fuentes y colores** . Por ejemplo, llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> método si se selecciona una nueva fuente.  
  
     o bien  
  
- Sondeo de los cambios en el IDE.  
  
     Esto puede realizarse a través de la interfaz implementada por el sistema <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Aunque principalmente para la compatibilidad con la persistencia, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> método se puede utilizar para obtener información de fuente y color para **Mostrar los elementos**. Para obtener más información, vea [acceso a la configuración de fuente y color almacenados](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    > Para asegurarse de que los resultados obtenidos mediante el sondeo son correctos, puede ser útil usar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz para determinar si se necesita un vaciado de caché y una actualización antes de llamar a los métodos de recuperación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Obtener información de fuente y color para la coloración del texto](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Obtener acceso a la configuración de fuente y color almacenada](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Cómo: obtener acceso a las fuentes integradas y a la combinación de colores](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Información general sobre fuentes y colores](../extensibility/font-and-color-overview.md)
