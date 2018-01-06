---
title: 'Tutorial: Crear un servicio de lenguaje heredado | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 660d33dd2d5c46d8020172c1fcf74bfb64b43360
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Tutorial: Crear un servicio de lenguaje heredado
Uso de las clases de lenguaje de managed package framework (MPF) para implementar un servicio de lenguaje en [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] es sencillo. Es necesario un VSPackage para hospedar el servicio de lenguaje, el propio servicio de lenguaje y un analizador en su idioma.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Ubicaciones de las plantillas de proyecto del paquete de Visual Studio  
 La plantilla de proyecto de paquete de Visual Studio puede encontrarse en tres ubicaciones de otra plantilla en el **nuevo proyecto** cuadro de diálogo:  
  
1.  En Extensibilidad de Visual Basic. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2.  En Extensibilidad de C#. El lenguaje predeterminado del proyecto es C#.  
  
3.  En otro tipos de extensibilidad del proyecto. El lenguaje predeterminado del proyecto es C++.  
  
### <a name="create-a-vspackage"></a>Crear un VSPackage  
  
1.  Crear un VSPackage nueva con la plantilla de proyecto de paquete de Visual Studio.  
  
     Si va a agregar un servicio de lenguaje para un VSPackage existente, omita los pasos siguientes y vaya directamente al procedimiento "Crear la clase de servicio de lenguaje".  
  
2.  Escriba MyLanguagePackage para el nombre del proyecto y haga clic en **Aceptar**.  
  
     Puede utilizar cualquier nombre que desee. Estos procedimientos que se describen aquí suponen MyLanguagePackage como el nombre.  
  
3.  Seleccione [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] como el idioma y la opción para generar un nuevo archivo de clave. Haga clic en **Siguiente**.  
  
4.  Escriba la información correspondiente de la empresa y el paquete. Haga clic en **Siguiente**.  
  
5.  Seleccione **comando de menú**. Haga clic en **Siguiente**.  
  
     Si no piensa admitir fragmentos de código, puede simplemente haga clic en Finalizar y omitir el paso siguiente.  
  
6.  Escriba **Insertar fragmento de código** como el **nombre del comando** y `cmdidInsertSnippet` para el **Id. de comando**. Haga clic en **Finalizar**.  
  
     El **nombre de comando** y **Id. de comando** puede ser todo lo que desees, estos son sólo algunos ejemplos.  
  
### <a name="create-the-language-service-class"></a>Crear la clase de servicio de lenguaje  
  
1.  En **el Explorador de soluciones**, haga doble clic en el proyecto MyLanguagePackage, elija **agregar**, **referencia**y, a continuación, elija la **agregar nueva referencia** botón.  
  
2.  En el **Agregar referencia** cuadro de diálogo, seleccione **Microsoft.VisualStudio.Package.LanguageService** en el **.NET** ficha y haga clic en **Aceptar**.  
  
     Esto debe realizarse una sola vez para el proyecto de paquete de idioma.  
  
3.  En **el Explorador de soluciones**, haga doble clic en el proyecto de VSPackage y seleccione **agregar**, **clase**.  
  
4.  Asegúrese de que **clase** está seleccionado en la lista de plantillas.  
  
5.  Escriba **MyLanguageService.cs** para el nombre del archivo de clase y haga clic en **agregar**.  
  
     Puede utilizar cualquier nombre que desee. Estos procedimientos que se describen aquí se suponen `MyLanguageService` como el nombre.  
  
6.  En el archivo MyLanguageService.cs, agregue las siguientes `using` instrucciones.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Modificar el `MyLanguageService` clase se deriva de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Coloque el cursor en "LanguageService" y de la **editar**, **IntelliSense** menú, seleccione **implementar clase abstracta**. Esto agrega los métodos mínimos necesarios para implementar una clase de servicio de lenguaje.  
  
9. Implementar los métodos abstractos, tal y como se describe en [implementar un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Registrar el servicio de lenguaje  
  
1.  Abra el archivo MyLanguagePackagePackage.cs y agregue las siguientes `using` instrucciones:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Registrar la clase de servicio de lenguaje, como se describe en [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md). Esto incluye las secciones de "Proffering el servicio de lenguaje" y los atributos de ProvideXX. Use MyLanguageService en este tema utiliza TestLanguageService.  
  
### <a name="the-parser-and-scanner"></a>El analizador y el analizador  
  
1.  Implementar un analizador y el escáner para su idioma, como se describe en [analizador del servicio de lenguaje heredado y el analizador](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Cómo implementar el analizador y el escáner es decisión suya y queda fuera del ámbito de este tema.  
  
## <a name="language-service-features"></a>Características del servicio de lenguaje  
 Para implementar cada característica en el servicio de lenguaje, se suele derivar una clase de la clase de servicio de idioma adecuada de MPF, implementan los métodos abstractos según sea necesario e invalidar los métodos adecuados. Qué clases creación y/o derivan depende de las características desea admitir. Estas características se describen en detalle en [características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md). El procedimiento siguiente es el enfoque general para derivar una clase de las clases MPF.  
  
#### <a name="deriving-from-an-mpf-class"></a>Derivar de una clase MPF  
  
1.  En **el Explorador de soluciones**, haga doble clic en el proyecto de VSPackage y seleccione **agregar**, **clase**.  
  
2.  Asegúrese de que **clase** está seleccionado en la lista de plantillas.  
  
     Escriba un nombre adecuado para el archivo de clase y haga clic en **agregar**.  
  
3.  En el nuevo archivo de clase, agregue las siguientes `using` instrucciones.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Modifique la clase se deriva de la clase MPF deseada.  
  
5.  Agregue un constructor de clase que tiene al menos los mismos parámetros que el constructor de la clase base y pasar los parámetros del constructor en el constructor de clase base.  
  
     Por ejemplo, el constructor para una clase derivada de la <xref:Microsoft.VisualStudio.Package.Source> clase podría ser similar al siguiente:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Desde el **editar**, **IntelliSense** menú, seleccione **implementar clase abstracta** si la clase base tiene los métodos abstractos que deben implementarse.  
  
7.  En caso contrario, colocar el símbolo de intercalación dentro de la clase y especifique el método que va a ser reemplazado.  
  
     Por ejemplo, escriba `public override` para ver una lista de todos los métodos que se pueden invalidar en esa clase.  
  
## <a name="see-also"></a>Vea también  
 [Implementar un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)