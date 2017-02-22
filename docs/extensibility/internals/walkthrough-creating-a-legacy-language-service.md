---
title: "Tutorial: Crear un servicio de lenguaje heredado | Microsoft Docs"
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
  - "Servicios de lenguaje [managed package framework], crear"
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Tutorial: Crear un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Mediante las clases de lenguaje administrado paquete framework \(MPF\) para implementar un servicio de lenguaje en [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] es sencillo. Es necesario un VSPackage para hospedar el servicio de lenguaje, el propio servicio de lenguaje y un analizador para su idioma.  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## Ubicaciones de la plantilla de proyecto de paquete de Visual Studio  
 La plantilla de proyecto de Visual Studio paquete pueden encontrarse en tres ubicaciones de plantilla diferente en el **nuevo proyecto** cuadro de diálogo:  
  
1.  En Extensibilidad de Visual Basic. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2.  En Extensibilidad de C\#. El lenguaje predeterminado del proyecto es C\#.  
  
3.  En Extensibilidad de Otros tipos de proyectos. El lenguaje predeterminado del proyecto es C\+\+.  
  
### Cree un VSPackage  
  
1.  Crear un VSPackage nueva con la plantilla de proyecto de paquete de Visual Studio.  
  
     Si va a agregar un servicio de lenguaje a un VSPackage existente, omita los pasos siguientes y vaya directamente al procedimiento "Crear la clase de servicio de lenguaje".  
  
2.  Escriba MyLanguagePackage para el nombre del proyecto y haga clic en **Aceptar**.  
  
     Puede utilizar cualquier nombre que desee. Estos procedimientos detallados aquí supone MyLanguagePackage como el nombre.  
  
3.  Seleccione [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] como el idioma y la opción para generar un archivo de clave. Haga clic en **Siguiente**.  
  
4.  Escriba la información correspondiente de la empresa y el paquete. Haga clic en **Siguiente**.  
  
5.  Seleccione **comando de menú**. Haga clic en **Siguiente**.  
  
     Si no desea admitir fragmentos de código, puede haga clic en Finalizar y omitir el paso siguiente.  
  
6.  Escriba **Insertar fragmento de código** como el **nombre de comando** y `cmdidInsertSnippet` para el **Id. de comando**. Haga clic en **Finalizar**.  
  
     El **nombre de comando** y **identificador de comando** puede ser que desees, éstos son sólo algunos ejemplos.  
  
### Crear la clase de servicio de lenguaje  
  
1.  En **el Explorador de soluciones**, haga doble clic en el proyecto MyLanguagePackage, elija **Agregar**, **referencia**, y, a continuación, elija la **Agregar nueva referencia** botón.  
  
2.  En el **Agregar referencia** cuadro de diálogo, seleccione **Microsoft.VisualStudio.Package.LanguageService** en el **.NET** y haga clic en **Aceptar**.  
  
     Esto debe realizarse una sola vez para el proyecto del paquete de idioma.  
  
3.  En **el Explorador de soluciones**, haga doble clic en el proyecto de VSPackage y seleccione **Agregar**, **clase**.  
  
4.  Asegúrese de que **clase** está seleccionado en la lista de plantillas.  
  
5.  Escriba **MyLanguageService.cs** para el nombre del archivo de clase y haga clic en **Agregar**.  
  
     Puede utilizar cualquier nombre que desee. Estos procedimientos detallados aquí se supone `MyLanguageService` como el nombre.  
  
6.  En el archivo MyLanguageService.cs, agregue la siguiente `using` instrucciones.  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Modificar la `MyLanguageService` clase se deriva de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase:  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Coloque el cursor en "LanguageService" y de la **Editar**, **IntelliSense** menú, seleccione **Implementar clase abstracta**. Esto agrega los métodos mínimos necesarios para implementar una clase de servicio de lenguaje.  
  
9. Implementar los métodos abstractos, tal como se describe en [Implementación de un servicio de lenguaje](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### Registrar el servicio de lenguaje  
  
1.  Abra el archivo MyLanguagePackagePackage.cs y agregue la siguiente `using` instrucciones:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Registrar la clase de servicio de lenguaje, como se describe en [Registrar un servicio de lenguaje](../../extensibility/internals/registering-a-legacy-language-service1.md). Esto incluye las secciones de "Proffering el servicio de lenguaje" y los atributos ProvideXX. Utilice MyLanguageService en este tema usa TestLanguageService.  
  
### El analizador y el analizador  
  
1.  Implementar un analizador y el escáner para su idioma, como se describe en [Escáneres y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Cómo implementar el analizador y el escáner es suya y queda fuera del ámbito de este tema.  
  
## Características del servicio de lenguaje  
 Para implementar cada característica en el servicio de lenguaje, se suele derivar una clase de la clase de servicio de lenguaje MPF adecuada, implementar los métodos abstractos según sea necesario e invalidar los métodos adecuados. Qué clases crear o derivan depende de las características que piensa admitir. Estas características se describen en detalle en [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md). El procedimiento siguiente es el enfoque general para derivar una clase de las clases MPF.  
  
#### Derivar de una clase MPF  
  
1.  En **el Explorador de soluciones**, haga doble clic en el proyecto de VSPackage y seleccione **Agregar**, **clase**.  
  
2.  Asegúrese de que **clase** está seleccionado en la lista de plantillas.  
  
     Escriba un nombre adecuado para el archivo de clase y haga clic en **Agregar**.  
  
3.  En el nuevo archivo de clase, agregue la siguiente `using` instrucciones.  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Modifique la clase se deriva de la clase MPF deseada.  
  
5.  Agregue un constructor de clase que tiene al menos los mismos parámetros que el constructor de clase base y pasar los parámetros del constructor en el constructor de clase base.  
  
     Por ejemplo, el constructor para una clase derivada de la <xref:Microsoft.VisualStudio.Package.Source> clase podría ser similar al siguiente:  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Desde el **Editar**, **IntelliSense** menú, seleccione **Implementar clase abstracta** si la clase base tiene los métodos abstractos que deben implementarse.  
  
7.  De lo contrario, coloque el símbolo de intercalación dentro de la clase y escriba el método se invalide.  
  
     Por ejemplo, escriba `public override` para ver una lista de todos los métodos que se pueden invalidar en esa clase.  
  
## Vea también  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)