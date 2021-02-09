---
title: Crear páginas de opciones | Microsoft Docs
description: Obtenga información sobre cómo crear una página de opciones en el menú herramientas de Visual Studio implementando una clase DialogPage desde el marco de trabajo de paquetes administrados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b01133e1f7daada2d9e2778c3966ccd66a81fd94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903163"
---
# <a name="create-options-pages"></a>Crear páginas de opciones
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Managed Package Framework, las clases derivadas de <xref:Microsoft.VisualStudio.Shell.DialogPage> extienden el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE agregando páginas de **Opciones** en el menú **herramientas** .

 Un objeto que implementa una determinada página de **Opciones de herramientas** está asociado con VSPackages específico por el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objeto.

 Dado que el entorno crea una instancia del objeto que implementa una página de **Opciones de herramientas** determinada cuando el IDE muestra esa página concreta:

- Una página de **Opciones de herramientas** debe implementarse en su propio objeto y no en el objeto que implementa un VSPackage.

- Un objeto no puede implementar varias páginas de **Opciones de herramientas** .

## <a name="register-as-a-tools-options-page-provider"></a>Registrar como proveedor de páginas de opciones de herramientas
 Un VSPackage que admite la configuración de usuario a través de las páginas de **Opciones de herramientas** indica los objetos que proporcionan estas páginas de **Opciones de herramientas** aplicando instancias de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> aplicadas a la <xref:Microsoft.VisualStudio.Shell.Package> implementación.

 Debe haber una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para cada <xref:Microsoft.VisualStudio.Shell.DialogPage> tipo derivado de que implementa una página de **Opciones de herramientas** .

 Cada instancia de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> usa el tipo que implementa la página **Opciones de herramientas** , las cadenas que contienen la categoría y la subcategoría usada para identificar una página **Opciones de herramientas** y la información de recursos para registrar el tipo como una página de opciones de **herramientas** .

## <a name="persist-tools-options-page-state"></a>Estado de la página Opciones de conservación de herramientas
 Si una implementación de la página **Opciones de herramientas** se registra con la compatibilidad con automatización habilitada, el IDE conserva el estado de la página junto con todas las demás páginas de **Opciones de herramientas** .

 Un VSPackage puede administrar su propia persistencia mediante el uso de <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Solo se debe usar uno u otro método de persistencia.

## <a name="implement-dialogpage-class"></a>Implementación de la clase DialogPage
 Un objeto que proporciona la implementación de un VSPackage de un <xref:Microsoft.VisualStudio.Shell.DialogPage> tipo derivado de puede aprovechar las siguientes características heredadas:

- Una ventana de interfaz de usuario predeterminada.

- Un mecanismo de persistencia predeterminado disponible si <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> se aplica a la clase, o si la <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> propiedad se establece en `true` para el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> que se aplica a la clase.

- Compatibilidad con la automatización.

  El requisito mínimo para un objeto que implementa una página de **Opciones de herramientas** mediante <xref:Microsoft.VisualStudio.Shell.DialogPage> es la adición de propiedades públicas.

  Si la clase se registró correctamente como un proveedor de páginas de **Opciones de herramientas** , las propiedades públicas estarán disponibles en la sección **Opciones** del menú **herramientas** en el formulario de una cuadrícula de propiedades.

  Todas estas características predeterminadas se pueden invalidar. Por ejemplo, para crear una interfaz de usuario más sofisticada, solo se requiere invalidar la implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .

## <a name="example"></a>Ejemplo
 A continuación se muestra una implementación simple de "Hola mundo" de una página de opciones. Al agregar el código siguiente a un proyecto predeterminado creado por la plantilla de paquete de Visual Studio con la opción de **comando de menú** seleccionada, se muestra de forma adecuada la funcionalidad de la página de opciones.

### <a name="description"></a>Descripción
 La siguiente clase define una página de opciones de "Hola mundo" mínima. Cuando se abre, el usuario puede establecer la `HelloWorld` propiedad pública en una cuadrícula de propiedades.

### <a name="code"></a>Código
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Descripción
 Al aplicar el siguiente atributo a la clase de paquete, la página Opciones estará disponible cuando se cargue el paquete. Los números son identificadores de recursos arbitrarios para la categoría y la página, y el valor booleano al final especifica si la página admite la automatización.

### <a name="code"></a>Código
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Descripción
 El siguiente controlador de eventos muestra un resultado en función del valor de la propiedad establecida en la página Opciones. Utiliza el <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> método con el resultado convertido explícitamente en el tipo de página de la opción personalizada para tener acceso a las propiedades expuestas por la página.

 En el caso de un proyecto generado por la plantilla de paquete, llame a esta función desde la `MenuItemCallback` función para adjuntarla al comando predeterminado agregado al menú **herramientas** .

### <a name="code"></a>Código
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Consulte también
- [Extender la configuración de usuario y las opciones](../../extensibility/extending-user-settings-and-options.md)
- [Compatibilidad de automatización con las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md)
