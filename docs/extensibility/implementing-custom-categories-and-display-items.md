---
title: "Implementaci&#243;n de categor&#237;as personalizadas y mostrar los elementos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de fuente y color [Visual Studio SDK], categorías"
  - "categorías personalizadas"
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementaci&#243;n de categor&#237;as personalizadas y mostrar los elementos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un VSPackage puede proporcionar un control de las fuentes y colores de texto que contiene a la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) a través de categorías personalizadas y mostrar los elementos.  
  
 Categorías personalizadas y mostrar los elementos que se encuentran en el **fuentes y colores** página de propiedades. Para abrir el **fuentes y colores** página de propiedades, en la **herramientas** menú, haga clic en **opciones**. Expanda **entorno** y, a continuación, haga clic en **fuentes y colores**.  
  
 Cuando se utiliza este mecanismo, paquetes VSPackage deben implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaz y sus interfaces asociadas.  
  
 En principio, este mecanismo puede utilizarse para modificar todo lo existente **Mostrar elementos** y **categorías** que contienen. Sin embargo, no debe utilizarse para modificar el **EditorCategory de texto** o su **Mostrar elementos**. Para obtener más información, vea [información general de Color y fuente](../extensibility/font-and-color-overview.md).  
  
 Para implementar personalizado **categorías** o **Mostrar elementos**, un VSPackage debe:  
  
-   Cree o identifique categorías en el registro.  
  
     Implementación del IDE de la **fuentes y colores** página de propiedades usa esta información para consultar correctamente para el servicio que admite una determinada categoría.  
  
-   Cree o identifique grupos (opcionales) en el registro.  
  
     Puede ser útil definir un grupo, que representa la unión de dos o más categorías. Si se define un grupo, el IDE combina subcategorías automáticamente y distribuye elementos para mostrar dentro del grupo.  
  
-   Implementar la compatibilidad con IDE.  
  
-   Controlar los cambios de fuente y color.  
  
 Para obtener información, consulte [acceso a fuentes almacenados y la configuración de Color](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Para crear o identificar categorías  
  
-   Construir un tipo especial de entrada de registro de la categoría en [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\< versión de Visual Studio>*\FontAndColors\\`<Category>`]  
  
     *\< categoría>* es el nombre no traducido de la categoría.  
  
-   Rellenar el registro con dos valores:  
  
    |Nombre|Tipo|Datos|Descripción|  
    |----------|----------|----------|-----------------|  
    |Categoría|REG_SZ|GUID|Crea un GUID para identificar la categoría.|  
    |Paquete|REG_SZ|GUID|El GUID del servicio de VSPackage que admite la categoría.|  
  
 El servicio especificado en el registro debe proporcionar una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> para la categoría correspondiente.  
  
## <a name="to-create-or-identify-groups"></a>Para crear o identificar los grupos  
  
-   Construir un tipo especial de entrada de registro de la categoría en [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\< versión de Visual Studio>*\FontAndColors\\*\< grupo>*]  
  
     *\< grupo>* es el nombre no traducido del grupo.  
  
-   Rellenar el registro con dos valores:  
  
    |Nombre|Tipo|Datos|Descripción|  
    |----------|----------|----------|-----------------|  
    |Categoría|REG_SZ|GUID|Crea un GUID para identificar el grupo.|  
    |Paquete|REG_SZ|GUID|El GUID del servicio que admite la categoría.|  
  
 El servicio especificado en el registro debe proporcionar una implementación de `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` para el grupo correspondiente.  
  
## <a name="to-implement-ide-support"></a>Para implementar la compatibilidad IDE  
  
-   Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, que devuelve un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaz o un `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaz para el IDE para cada **categoría** o grupo GUID proporcionado.  
  
-   Para cada **categoría** lo admite, un VSPackage implementa una instancia independiente de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaz.  
  
-   Los métodos que se implementan a través de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> debe proporcionar el IDE con:  
  
    -   Listas de **Mostrar elementos** en el **categoría.**  
  
    -   Nombres localizables para **Mostrar elementos**.  
  
    -   Mostrar información de cada miembro de **categoría**.  
  
    > [!NOTE]
    >  Cada **categoría** debe contener al menos un **elemento para mostrar**.  
  
-   El IDE usa la `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaz para definir una unión de varias categorías.  
  
     Su implementación proporciona el IDE con:  
  
    -   Una lista de los **categorías** que forman parte de un grupo determinado.  
  
    -   Acceso a las instancias de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> admitir cada **categoría** dentro del grupo.  
  
    -   Nombres de grupo localizable.  
  
-   Actualizando el IDE:  
  
     El IDE se almacena en caché información acerca de **fuente y Color** configuración. Por lo tanto, después de realizar cualquier modificación del IDE **fuente y Color** configuración, es aconsejable para asegurarse de que la memoria caché está actualizada.  
  
 Actualización de la memoria caché se efectúa a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> de interfaz y puede estar compuesta por elementos seleccionado globalmente o simplemente en realizada.  
  
## <a name="to-handle-font-and-color-changes"></a>Para controlar la fuente y Color cambia  
 Para ser compatibles con el color del texto que muestra un paquete VSPackage, el servicio de colores que admite el VSPackage debe responder a los cambios iniciada por el usuario que se realizan a través de la **fuentes y colores** página de propiedades. Un VSPackage para ello:  
  
-   Control de eventos generados por el IDE implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfaz.  
  
     El IDE llama al método adecuado después de las modificaciones de usuario de la **fuentes y colores** página. Por ejemplo, llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> método si se selecciona una fuente nueva.  
  
     O bien  
  
-   El IDE para cambios de sondeo.  
  
     Esto puede hacerse mediante el implementado por el sistema <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz. Aunque principalmente para la compatibilidad de persistencia, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> método se puede utilizar para obtener información de fuente y color de **Mostrar elementos**. Para obtener más información, vea [acceso a fuentes almacenados y la configuración de Color](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    >  Para garantizar que los resultados obtenidos mediante sondeo son correctos, puede ser útil usar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz para determinar si se necesitan un vaciado de la caché y la actualización antes de llamar a los métodos de recuperación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Obtención de fuente y la información de Color para el color de texto](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Obtener acceso a la configuración de Color y fuente almacenado](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Cómo: obtener acceso a las fuentes integradas y la combinación de colores](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Información general de Color y fuente](../extensibility/font-and-color-overview.md)