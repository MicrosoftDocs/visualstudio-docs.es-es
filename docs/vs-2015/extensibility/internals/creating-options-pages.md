---
title: Crear páginas de opciones | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff543e0b75b4bd1ca09068f6de7b62248c515158
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579786"
---
# <a name="creating-options-pages"></a>Creación de páginas de opciones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [crear páginas de opciones](https://docs.microsoft.com/visualstudio/extensibility/internals/creating-options-pages).  
  
En el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] marco de trabajo de paquetes administrados, las clases derivadas de <xref:Microsoft.VisualStudio.Shell.DialogPage> ampliar el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE mediante la adición de **opciones** páginas bajo la **herramientas** menú.  
  
 Un objeto que implementa un determinado **herramientas-opciones** página está asociada a VSPackages específicos por el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objeto.  
  
 Dado que el entorno crea una instancia del objeto que implementa un determinado **opciones de herramientas** página cuando se muestra la página determinada por el IDE:  
  
-   Un **herramientas-opciones** página debe implementarse en su propio objeto y no en el objeto que implementa un paquete VSPackage.  
  
-   Un objeto no puede implementar varios **opciones de herramientas** páginas.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Cómo registrar un proveedor de página de opciones de herramientas  
 Una configuración de usuario de apoyo de VSPackage a través de **herramientas-opciones** páginas indica los objetos proporcionándoselas **herramientas-opciones** páginas aplicando las instancias de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> aplicado a la <xref:Microsoft.VisualStudio.Shell.Package>implementación.  
  
 Debe haber una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para cada <xref:Microsoft.VisualStudio.Shell.DialogPage>-derivadas de tipo que implementa un **opciones de herramientas** página.  
  
 Cada instancia de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> usa el tipo que implementa el **herramientas-opciones** página, las cadenas que contienen la categoría y subcategoría que se usa para identificar un **herramientas-opciones** página y recursos información para registrar el tipo como proporcionar un **opciones de herramientas** página.  
  
## <a name="persisting-tools-options-page-state"></a>Conservar el estado de las herramientas de las opciones de página  
 Si un **herramientas-opciones** implementación de la página se registra con compatibilidad de automatización habilitada, el IDE conserva el estado de la página, junto con todos los demás **opciones de herramientas** páginas.  
  
 Un VSPackage puede administrar su propia persistencia mediante <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Se debe usar solo uno o el otro método de persistencia.  
  
## <a name="implementing-dialogpage-class"></a>Implementación de clase de DialogPage  
 Un objeto que proporciona una implementación de un VSPackage un <xref:Microsoft.VisualStudio.Shell.DialogPage>-tipo derivado puede aprovechar las ventajas de las siguientes características heredadas:  
  
-   Una ventana de interfaz de usuario de forma predeterminada.  
  
-   Predeterminado de un mecanismo de persistencia disponible cualquier if <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> se aplica a la clase, o si el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> propiedad está establecida en `true` para el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> que se aplica a la clase.  
  
-   Compatibilidad de automatización.  
  
 El requisito mínimo para un objeto que implementa un **herramientas-opciones** página utilizando <xref:Microsoft.VisualStudio.Shell.DialogPage> es la adición de propiedades públicas.  
  
 Si la clase ha registrado correctamente como un **herramientas-opciones** página proveedor, sus propiedades públicas están disponibles en el **opciones** sección de la **herramientas** menú en forma de un cuadrícula de propiedades.  
  
 Todas estas características predeterminado pueden invalidarse. Por ejemplo, para crear un usuario más sofisticado interfaz requiere sólo reemplazar la implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Ejemplo  
 Lo que sigue es una implementación sencilla "Hola mundo" de una página de opciones. Agregue el código siguiente a un proyecto predeterminado creado por la plantilla de paquete de Visual Studio con el **comando de menú** opción seleccionada adecuadamente demostrará la funcionalidad de la página de opción.  
  
### <a name="description"></a>Descripción  
 La siguiente clase define una página de opciones mínima "Hola mundo". Cuando se abre, el usuario puede establecer el público `HelloWorld` propiedad en una cuadrícula de propiedades.  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Descripción  
 Aplicar el atributo siguiente a la clase de paquete hace que las opciones de página estén disponibles cuando se carga el paquete. Los números son identificadores de recursos arbitrarios para la categoría y la página y el valor booleano al final especifica si admite la automatización de la página.  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Descripción  
 El siguiente controlador de eventos muestra resultado en función del valor de la propiedad establecida en la página de opciones. Usa el <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> método con el resultado de convertir explícitamente en el tipo de página de la opción personalizada para tener acceso a las propiedades expuestas por la página.  
  
 En el caso de un proyecto generado por la plantilla de paquete, llame a esta función desde el `MenuItemCallback` función asociarlo al comando predeterminado se agrega a la **herramientas** menú.  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>Vea también  
 [Opciones y configuración de usuario de extensión](../../extensibility/extending-user-settings-and-options.md)   
 [Compatibilidad de automatización para las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md)

