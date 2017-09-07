---
title: "Crear páginas de opciones | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 6ed61dbc745b00f5f6f0beeba5aa38c3d316f98f
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="creating-options-pages"></a>Crear páginas de opciones
En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] marco de trabajo de paquetes administrados, las clases derivadas de <xref:Microsoft.VisualStudio.Shell.DialogPage> ampliar la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE agregando **opciones** páginas en el **herramientas** menú.  
  
 Un objeto que implementa un determinado **la opción herramientas** página está asociada a VSPackages específicos por el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objeto.  
  
 Dado que el entorno crea el objeto que implementa un determinado **opciones de herramientas** página cuando se muestra la página determinada por el IDE:  
  
-   A **la opción herramientas** página debe implementarse en su propio objeto y no en el objeto que implementa un paquete VSPackage.  
  
-   Un objeto no puede implementar varios **opciones de herramientas** páginas.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Registrar como un proveedor de página de opciones de herramientas  
 Una configuración de usuario de apoyo de VSPackage a través de **opciones de herramientas** páginas indica los objetos proporcionándoselas **opciones de herramientas** páginas aplicando instancias de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> aplicado a la <xref:Microsoft.VisualStudio.Shell.Package>implementación.  
  
 Debe haber una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para cada <xref:Microsoft.VisualStudio.Shell.DialogPage>-deriva el tipo que implementa un **opciones de herramientas** página.  
  
 Cada instancia de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utiliza el tipo que implementa el **opciones de herramientas** página, las cadenas que contienen la categoría y subcategoría usado para identificar un **opciones de herramientas** página y recursos información para registrar el tipo que proporciona un **opciones de herramientas** página.  
  
## <a name="persisting-tools-options-page-state"></a>Guardar estado de página de opciones de herramientas  
 Si un **opciones de herramientas** implementación de la página está registrado con habilitada la compatibilidad con automatización, el IDE conserva el estado de la página junto con todos los demás **opciones de herramientas** páginas.  
  
 Un VSPackage puede administrar su propia persistencia mediante <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Debe utilizarse solo uno o el otro método de persistencia.  
  
## <a name="implementing-dialogpage-class"></a>Clase de implementación DialogPage  
 Objeto que proporciona la implementación de un paquete VSPackage de un <xref:Microsoft.VisualStudio.Shell.DialogPage>-tipo derivado puede aprovechar las ventajas de las siguientes características heredadas:  
  
-   Una ventana de interfaz de usuario de forma predeterminada.  
  
-   Predeterminado de un mecanismo de persistencia disponible cualquier if <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> se aplica a la clase, o si la <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> propiedad está establecida en `true` para el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> que se aplica a la clase.  
  
-   Compatibilidad de automatización.  
  
 El requisito mínimo para un objeto que implementa un **opciones de herramientas** página con <xref:Microsoft.VisualStudio.Shell.DialogPage> es la adición de propiedades públicas.  
  
 Si la clase ha registrado correctamente como un **opciones de herramientas** página proveedor, sus propiedades públicas están disponibles en la **opciones** sección de la **herramientas** menú en forma de un cuadrícula de propiedades.  
  
 Todas estas características de forma predeterminada se pueden invalidar. Por ejemplo, para crear un usuario más sofisticado interfaz requiere sólo reemplazar la implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Ejemplo  
 La información siguiente es una implementación simple "Hola a todos" de una página de opciones. Agregue el código siguiente a un proyecto predeterminado creado por la plantilla de paquete de Visual Studio con la **comando de menú** opción seleccionada adecuadamente mostrarán la funcionalidad de la página de opción.  
  
### <a name="description"></a>Descripción  
 La siguiente clase define una página de opciones de "Hola a todos" mínima. Cuando se abre, el usuario puede establecer el público `HelloWorld` propiedad en una cuadrícula de propiedades.  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages #11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs) ] [!code-vb [UI_UserSettings_ToolsOptionPages Nº 11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Descripción  
 Aplicar el atributo siguiente a la clase de paquete hace que las opciones de página estén disponibles al cargar el paquete. Los números son arbitrario Id. de recurso para la categoría y la página, y el valor booleano al final especifica si la página admite la automatización.  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages #07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs) ] [!code-vb [UI_UserSettings_ToolsOptionPages #07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Descripción  
 El siguiente controlador de eventos muestra resultado dependiendo del valor de la propiedad establecida en la página de opciones. Usa el <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> método con el resultado de convertir explícitamente en el tipo de página de la opción personalizada para tener acceso a las propiedades expuestas por la página.  
  
 En el caso de un proyecto generado por la plantilla de paquete, llame a esta función desde la `MenuItemCallback` función para adjuntar al comando de forma predeterminada se agrega a la **herramientas** menú.  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages #08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs) ] [!code-vb [UI_UserSettings_ToolsOptionPages #08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Vea también  
 [Opciones y configuración de usuario de extensión](../../extensibility/extending-user-settings-and-options.md)   
 [Compatibilidad de automatización para las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md)
