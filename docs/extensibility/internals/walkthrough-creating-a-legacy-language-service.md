---
title: 'Tutorial: Creación de un servicio de lenguaje heredado ( Legacy Language Service) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703686"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Tutorial: Creación de un servicio de lenguaje heredado
El uso de las clases de lenguaje del [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] marco de paquetes administrados (MPF) para implementar un servicio de lenguaje es sencillo. Necesita un VSPackage para hospedar el servicio de lenguaje, el propio servicio de lenguaje y un analizador para el idioma.

## <a name="prerequisites"></a>Prerrequisitos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea SDK de [Visual Studio](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Ubicaciones de la plantilla de proyecto de paquete de Visual Studio
 La plantilla de proyecto de paquete de Visual Studio se puede encontrar en tres ubicaciones de plantilla diferentes en el cuadro de diálogo **Nuevo proyecto:**

1. En Extensibilidad de Visual Basic. El lenguaje predeterminado del proyecto es Visual Basic.

2. En Extensibilidad de C#. El lenguaje predeterminado del proyecto es C#.

3. En otro tipos de extensibilidad del proyecto. El lenguaje predeterminado del proyecto es C++.

### <a name="create-a-vspackage"></a>Crear un VSPackage

1. Crear un nuevo VSPackage con el paquete de Visual Studio plantilla de proyecto.

    Si va a agregar un servicio de lenguaje a un VSPackage existente, omita los pasos siguientes y vaya directamente al procedimiento "Crear la clase de servicio de lenguaje".

2. Escriba MyLanguagePackage para el nombre del proyecto y haga clic en **Aceptar**.

    Puedes usar el nombre que quieras. Estos procedimientos detallados aquí asumen MyLanguagePackage como el nombre.

3. Seleccione [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] como idioma y la opción para generar un nuevo archivo de claves. Haga clic en **Next**.

4. Introduzca la información de la empresa y del paquete correspondiente. Haga clic en **Next**.

5. Seleccione **Comando de menú**. Haga clic en **Next**.

    Si no tiene la intención de admitir fragmentos de código, puede hacer clic en Finalizar e ignorar el paso siguiente.

6. Ingrese el fragmento de `cmdidInsertSnippet` la **inserción** como el nombre del **comando** y para el ID de **comando**. Haga clic en **Finalizar**

    El nombre de **comando** y el **identificador** de comando pueden ser lo que desee, estos son solo ejemplos.

### <a name="create-the-language-service-class"></a>Crear la clase de servicio de lenguaje

1. En el **Explorador**de soluciones , haga clic con el botón secundario en el proyecto MyLanguagePackage, elija **Agregar**, **Referencia**y, a continuación, elija el botón Agregar **nueva referencia** .

2. En el cuadro de diálogo **Agregar referencia** , seleccione **Microsoft.VisualStudio.Package.LanguageService** en la pestaña **.NET** y haga clic en **Aceptar**.

     Esto debe hacerse solo una vez para el proyecto de paquete de idioma.

3. En **el Explorador**de soluciones , haga clic con el botón secundario en el proyecto VSPackage y seleccione **Agregar**, **Clase**.

4. Asegúrese de que **Clase** está seleccionada en la lista de plantillas.

5. Escriba **MyLanguageService.cs** para el nombre del archivo de clase y haga clic en **Agregar**.

     Puedes usar el nombre que quieras. Estos procedimientos `MyLanguageService` detallados aquí asumen como el nombre.

6. En el archivo MyLanguageService.cs, `using` agregue las siguientes directivas.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Modifique `MyLanguageService` la clase para <xref:Microsoft.VisualStudio.Package.LanguageService> derivar de la clase:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Coloque el cursor en "LanguageService" y, en el menú **Editar**, **IntelliSense,** seleccione **Implementar clase abstracta**. Esto agrega los métodos mínimos necesarios para implementar una clase de servicio de lenguaje.

9. Implemente los métodos abstractos como se describe en [Implementación de un servicio](../../extensibility/internals/implementing-a-legacy-language-service2.md)de lenguaje heredado .

### <a name="register-the-language-service"></a>Registrar el servicio de idiomas

1. Abra el archivo MyLanguagePackagePackage.cs `using` y agregue las siguientes directivas:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Registre la clase de servicio de lenguaje como se describe en [Registro de un servicio](../../extensibility/internals/registering-a-legacy-language-service1.md)de lenguaje heredado . Esto incluye las secciones ProvideXX attributes y "Proffering the Language Service". Use MyLanguageService donde este tema usa TestLanguageService.

### <a name="the-parser-and-scanner"></a>El analizador y el escáner

1. Implemente un analizador y un analizador para su idioma como se describe en Analizador y analizador de servicios de [lenguaje heredado.](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

     La forma de implementar el analizador y el analizador depende totalmente de usted y está fuera del alcance de este tema.

## <a name="language-service-features"></a>Características del servicio de idiomas
 Para implementar cada característica en el servicio de lenguaje, normalmente deriva una clase de la clase de servicio de lenguaje MPF adecuada, implementa los métodos abstractos según sea necesario e invalida los métodos adecuados. Las clases que cree y/o de las que derive dependerán de las características que desee admitir. Estas características se describen en detalle en Características del servicio de [lenguaje heredado.](../../extensibility/internals/legacy-language-service-features1.md) El siguiente procedimiento es el enfoque general para derivar una clase de las clases MPF.

#### <a name="deriving-from-an-mpf-class"></a>Derivado de una clase MPF

1. En **el Explorador**de soluciones , haga clic con el botón secundario en el proyecto VSPackage y seleccione **Agregar**, **Clase**.

2. Asegúrese de que **Clase** está seleccionada en la lista de plantillas.

     Escriba un nombre adecuado para el archivo de clase y haga clic en **Agregar**.

3. En el nuevo archivo de `using` clase, agregue las siguientes directivas.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Modifique la clase para derivar de la clase MPF deseada.

5. Agregue un constructor de clase que tome al menos los mismos parámetros que el constructor de la clase base y pase los parámetros del constructor al constructor de la clase base.

     Por ejemplo, el constructor de una <xref:Microsoft.VisualStudio.Package.Source> clase derivada de la clase podría tener el siguiente aspecto:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. En el menú **Editar**, **IntelliSense,** seleccione **Implementar clase abstracta** si la clase base tiene métodos abstractos que se deben implementar.

7. De lo contrario, coloque el intercalador dentro de la clase e introduzca el método que se va a invalidar.

     Por ejemplo, `public override` escriba para ver una lista de todos los métodos que se pueden invalidar en esa clase.

## <a name="see-also"></a>Vea también
- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
