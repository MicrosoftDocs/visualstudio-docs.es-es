---
title: Creación de páginas de opciones ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709144"
---
# <a name="create-options-pages"></a>Crear páginas de opciones
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el marco de paquete <xref:Microsoft.VisualStudio.Shell.DialogPage> administrado, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las clases derivadas de ampliar el IDE **agregando** opciones páginas en el **herramientas** menú.

 Un objeto que implementa una determinada página de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> opción de **herramientas** está asociado con VSPackages específicos por el objeto.

 Dado que el entorno crea una instancia del objeto que implementa una página **de opciones** de herramientas determinada cuando el IDE muestra esa página determinada:

- Un **opciones** de herramientas página debe implementarse en su propio objeto y no en el objeto que implementa un VSPackage.

- Un objeto no puede implementar varias páginas **Opciones** de herramientas.

## <a name="register-as-a-tools-options-page-provider"></a>Regístrese como proveedor de páginas Opciones de herramientas
 Un VSPackage que admite la configuración de usuario a través **de opciones** de herramientas páginas indica los objetos que proporcionan estas páginas de opciones de **herramientas** mediante la aplicación de instancias de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> aplicado a la <xref:Microsoft.VisualStudio.Shell.Package> implementación.

 Debe haber una <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> instancia <xref:Microsoft.VisualStudio.Shell.DialogPage>de cada tipo derivado que implemente una página **Opciones** de herramientas.

 Cada instancia <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> de utiliza el tipo que implementa la página **Opciones** de herramientas, las cadenas que contienen la categoría y la subcategoría utilizadas para identificar una página **Opciones** de herramientas e información de recursos para registrar el tipo como una página **Opciones** de herramientas.

## <a name="persist-tools-options-page-state"></a>Estado de la página Opciones de herramientas de persistencia
 Si se registra una implementación de página **Opciones** de herramientas con compatibilidad con automatización habilitada, el IDE conserva el estado de la página junto con todas las demás páginas **Opciones** de herramientas.

 Un VSPackage puede administrar su <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>propia persistencia mediante . Solo se debe utilizar uno u otro método de persistencia.

## <a name="implement-dialogpage-class"></a>Implementar la clase DialogPage
 Un objeto que proporciona la implementación de un VSPackage de un <xref:Microsoft.VisualStudio.Shell.DialogPage>tipo derivado puede aprovechar las siguientes características heredadas:

- Una ventana de interfaz de usuario predeterminada.

- Un mecanismo de persistencia <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> predeterminado disponible si se <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> aplica a `true` la <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> clase o si la propiedad se establece en para la que se aplica a la clase.

- Soporte de automatización.

  El requisito mínimo para **Tools Options** un objeto <xref:Microsoft.VisualStudio.Shell.DialogPage> que implementa una página Opciones de herramientas mediante es la adición de propiedades públicas.

  Si la clase se registra correctamente como proveedor de **páginas Opciones** de herramientas, sus propiedades públicas están disponibles en la sección **Opciones** del menú **Herramientas** en forma de cuadrícula de propiedades.

  Todas estas características predeterminadas se pueden invalidar. Por ejemplo, para crear una interfaz de usuario más <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>sofisticada solo se requiere reemplazar la implementación predeterminada de .

## <a name="example"></a>Ejemplo
 Lo que sigue es una simple implementación "Hola mundo" de una página de opciones. Agregar el código siguiente a un proyecto predeterminado creado por la plantilla de paquete de Visual Studio con la opción **Comando** de menú seleccionada demostrará adecuadamente la funcionalidad de la página de opciones.

### <a name="description"></a>Descripción
 La siguiente clase define una página de opciones mínima "Hola mundo". Cuando se abre, el `HelloWorld` usuario puede establecer la propiedad pública en una cuadrícula de propiedades.

### <a name="code"></a>Código
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Descripción
 Aplicar el siguiente atributo a la clase de paquete hace que la página de opciones esté disponible cuando se carga el paquete. Los números son identificadores de recursos arbitrarios para la categoría y la página, y el valor booleano al final especifica si la página admite la automatización.

### <a name="code"></a>Código
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Descripción
 El siguiente controlador de eventos muestra un resultado en función del valor del conjunto de propiedades en la página de opciones. Utiliza el <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> método con el resultado explícitamente conviertedo en el tipo de página de opción personalizada para tener acceso a las propiedades expuestas por la página.

 En el caso de un proyecto generado por la `MenuItemCallback` plantilla de paquete, llame a esta función desde la función para adjuntarla al comando predeterminado agregado al menú **Herramientas.**

### <a name="code"></a>Código
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Vea también
- [Ampliar la configuración y las opciones del usuario](../../extensibility/extending-user-settings-and-options.md)
- [Soporte de automatización para páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md)
