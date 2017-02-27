---
title: "Crear p&#225;ginas de opciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "marco de trabajo de paquete administrados, crear páginas de opciones de herramientas"
  - "Páginas de opciones de herramientas [Visual Studio SDK], crear mediante administra el marco de trabajo de paquete"
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Crear p&#225;ginas de opciones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] framework paquete administrados, las clases derivadas de <xref:Microsoft.VisualStudio.Shell.DialogPage> ampliar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE agregando **opciones** páginas bajo la **herramientas** menú.  
  
 Un objeto que implementa una determinada **opción herramientas** página está asociada a VSPackages específico por el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objeto.  
  
 Dado que el entorno crea el objeto que implementa una determinada **Opciones de herramientas** página cuando se muestra la página determinada por el IDE:  
  
-   Un **opción herramientas** página debe implementarse en su propio objeto y no en el objeto que implementa un VSPackage.  
  
-   Un objeto no puede implementar varios **Opciones de herramientas** páginas.  
  
## Registrar como un proveedor de página de opciones de herramientas  
 Una configuración de usuario de VSPackage apoyo a través de **Opciones de herramientas** páginas indica los objetos que proporciona estos **Opciones de herramientas** páginas aplicando instancias de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> aplicado a la <xref:Microsoft.VisualStudio.Shell.Package> implementación.  
  
 Debe haber una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para cada <xref:Microsoft.VisualStudio.Shell.DialogPage>\-deriva el tipo que implementa un **Opciones de herramientas** página.  
  
 Cada instancia de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utiliza el tipo que implementa el **Opciones de herramientas** cadenas que contienen la categoría y subcategoría usado para identificar la página un **Opciones de herramientas** página e información de recursos para registrar el tipo como proporcionar un **Opciones de herramientas** página.  
  
## Estado de la página de opciones de herramientas persistentes  
 Si un **Opciones de herramientas** implementación de página está registrado con compatibilidad de automatización habilitado, el IDE conserva el estado de la página junto con todos los demás **Opciones de herramientas** páginas.  
  
 Un VSPackage puede administrar su propia persistencia mediante <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Debe utilizarse solo uno o el otro método de persistencia.  
  
## Clase de implementación DialogPage  
 Objeto que proporciona la implementación de un paquete VSPackage de un <xref:Microsoft.VisualStudio.Shell.DialogPage>\-tipo derivado puede aprovechar las siguientes características heredadas:  
  
-   Una ventana de interfaz de usuario de forma predeterminada.  
  
-   Predeterminado de un mecanismo de persistencia disponible cualquiera <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> se aplica a la clase, o si el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> propiedad está establecida en `true` para el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> que se aplica a la clase.  
  
-   Compatibilidad de automatización.  
  
 El requisito mínimo para un objeto que implementa un **Opciones de herramientas** página con <xref:Microsoft.VisualStudio.Shell.DialogPage> es la adición de propiedades públicas.  
  
 Si la clase ha registrado correctamente como un **Opciones de herramientas** página proveedor, sus propiedades públicas están disponibles en la **opciones** sección de la **herramientas** menú en forma de una cuadrícula de propiedades.  
  
 Todas estas características de forma predeterminada, se pueden invalidar. Por ejemplo, para crear un usuario más sofisticado interfaz requiere sólo reemplazar la implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## Ejemplo  
 Lo que sigue es una implementación simple "hello world" de una página de opciones. Agregue el código siguiente a un proyecto predeterminado creado por la plantilla de paquete de Visual Studio con el **comando de menú** opción seleccionada adecuadamente demostrará la funcionalidad de la página de opción.  
  
### Descripción  
 La siguiente clase define una página de opciones de "Hola a todos" mínima. Cuando se abre, el usuario puede establecer el público `HelloWorld` propiedad en una cuadrícula de propiedades.  
  
### Código  
 [!code-cs[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### Descripción  
 Aplicar el atributo siguiente a la clase de paquete hace que las opciones de página disponible al cargar el paquete. Los números son identificadores de recursos arbitrarios para la categoría y la página y el valor booleano al final especifica si la página admite la automatización.  
  
### Código  
 [!code-cs[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### Descripción  
 El siguiente controlador de eventos muestra resultado en función del valor de la propiedad establecida en la página Opciones. Usa el <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> método con el resultado de convertir explícitamente en el tipo de página de la opción personalizada para tener acceso a las propiedades expuestas por la página.  
  
 En el caso de un proyecto generado por la plantilla de paquete, llame a esta función desde el `MenuItemCallback` función adjuntar al comando de forma predeterminada se agrega a la **herramientas** menú.  
  
### Código  
 [!code-cs[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## Vea también  
 [Opciones y configuración de usuario de extensión](../../extensibility/extending-user-settings-and-options.md)   
 [Compatibilidad de automatización para las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md)