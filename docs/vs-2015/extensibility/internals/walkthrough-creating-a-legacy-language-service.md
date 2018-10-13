---
title: 'Tutorial: Crear un servicio de lenguaje heredado | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 996806b1a15d6e7b45204a954c58b153e33a4be4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220056"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Tutorial: Creación de un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mediante las clases de lenguaje de framework (MPF) paquete administrado para implementar un servicio de lenguaje en [!INCLUDE[csprcs](../../includes/csprcs-md.md)] es sencillo. Necesita un VSPackage para hospedar el servicio de lenguaje, el servicio de lenguaje propio y un analizador para su idioma.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Ubicaciones de las plantillas de proyecto del paquete de Visual Studio  
 La plantilla de proyecto de paquete de Visual Studio puede encontrarse en tres ubicaciones diferentes de plantilla en el **nuevo proyecto** cuadro de diálogo:  
  
1.  En Extensibilidad de Visual Basic. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2.  En Extensibilidad de C#. El lenguaje predeterminado del proyecto es C#.  
  
3.  En otro tipos de extensibilidad del proyecto. El lenguaje predeterminado del proyecto es C++.  
  
### <a name="create-a-vspackage"></a>Crear un VSPackage  
  
1.  Cree un nuevo paquete de VS con la plantilla de proyecto de paquete de Visual Studio.  
  
     Si va a agregar un servicio de lenguaje a un VSPackage existente, omita los pasos siguientes y vaya directamente al procedimiento "Crear la clase de servicio de lenguaje".  
  
2.  Escriba MyLanguagePackage para el nombre del proyecto y haga clic en **Aceptar**.  
  
     Puede utilizar cualquier nombre que desee. Estos procedimientos detallados aquí suponen MyLanguagePackage como el nombre.  
  
3.  Seleccione [!INCLUDE[csprcs](../../includes/csprcs-md.md)] como el idioma y la opción para generar un nuevo archivo de clave. Haga clic en **Siguiente**.  
  
4.  Escriba la información correspondiente de la empresa y el paquete. Haga clic en **Siguiente**.  
  
5.  Seleccione **comando de menú**. Haga clic en **Siguiente**.  
  
     Si no desea utilizar con fragmentos de código, puede haga clic en Finalizar y omitir el paso siguiente.  
  
6.  Escriba **Insertar fragmento de código** como el **nombre de comando** y `cmdidInsertSnippet` para el **identificador de comando**. Haga clic en **Finalizar**.  
  
     El **nombre de comando** y **identificador de comando** puede ser lo que quiera, estos son solo ejemplos.  
  
### <a name="create-the-language-service-class"></a>Crear la clase de servicio de lenguaje  
  
1.  En **el Explorador de soluciones**, haga doble clic en el proyecto MyLanguagePackage, elija **agregar**, **referencia**y, a continuación, elija el **agregar nueva referencia** botón.  
  
2.  En el **Agregar referencia** cuadro de diálogo, seleccione **Microsoft.VisualStudio.Package.LanguageService** en el **.NET** ficha y haga clic en **Aceptar**.  
  
     Esto debe realizarse una sola vez para el proyecto de paquete de idioma.  
  
3.  En **el Explorador de soluciones**, haga doble clic en el proyecto VSPackage y seleccione **agregar**, **clase**.  
  
4.  Asegúrese de que **clase** está seleccionado en la lista de plantillas.  
  
5.  Escriba **MyLanguageService.cs** para el nombre del archivo de clase y haga clic en **agregar**.  
  
     Puede utilizar cualquier nombre que desee. Estos procedimientos detallados aquí se supone `MyLanguageService` como el nombre.  
  
6.  En el archivo MyLanguageService.cs, agregue la siguiente `using` instrucciones.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs#1)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb#1)]  
  
7.  Modificar el `MyLanguageService` clase derive de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs#2)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb#2)]  
  
8.  Coloque el cursor en "LanguageService" y desde el **editar**, **IntelliSense** menú, seleccione **implementar clase abstracta**. Esto agrega los métodos necesarios mínimos para implementar una clase de servicio de lenguaje.  
  
9. Implementar los métodos abstractos, tal como se describe en [implementar un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Registrar el servicio de lenguaje  
  
1.  Abra el archivo MyLanguagePackagePackage.cs y agregue las siguientes `using` instrucciones:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguagepackagepackage.cs#3)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguagepackagepackage.vb#3)]  
  
2.  Registrar la clase de servicio de lenguaje, como se describe en [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md). Esto incluye los atributos de ProvideXX y secciones de "Proffering el servicio de lenguaje". Use MyLanguageService en este tema usa TestLanguageService.  
  
### <a name="the-parser-and-scanner"></a>El analizador y el analizador  
  
1.  Implementar un analizador y el analizador para su idioma, como se describe en [analizador del servicio de lenguaje heredado y el analizador](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Cómo implementar el analizador y el escáner es totalmente suya y queda fuera del ámbito de este tema.  
  
## <a name="language-service-features"></a>Características del servicio de lenguaje  
 Para implementar cada característica en el servicio de lenguaje, se suele derivar una clase de la clase de servicio de lenguaje MPF adecuada, implementan todos los métodos abstractos según sea necesario e invalide los métodos adecuados. Qué clases crear y/o derivan depende de las características que piensa admitir. Estas características se tratan detalladamente en [características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md). El siguiente procedimiento es el enfoque general para derivar una clase de las clases MPF.  
  
#### <a name="deriving-from-an-mpf-class"></a>Derivar una clase MPF  
  
1.  En **el Explorador de soluciones**, haga doble clic en el proyecto VSPackage y seleccione **agregar**, **clase**.  
  
2.  Asegúrese de que **clase** está seleccionado en la lista de plantillas.  
  
     Escriba un nombre adecuado para el archivo de clase y haga clic en **agregar**.  
  
3.  En el nuevo archivo de clase, agregue la siguiente `using` instrucciones.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs#4)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb#4)]  
  
4.  Modifique la clase que derive de la clase MPF deseada.  
  
5.  Agregue un constructor de clase que tiene al menos los mismos parámetros que el constructor de clase base y pasar los parámetros del constructor en el constructor de clase base.  
  
     Por ejemplo, el constructor para una clase derivada de la <xref:Microsoft.VisualStudio.Package.Source> clase podría ser similar al siguiente:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs#5)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb#5)]  
  
6.  Desde el **editar**, **IntelliSense** menú, seleccione **implementar clase abstracta** si la clase base tiene todos los métodos abstractos que deben implementarse.  
  
7.  En caso contrario, coloque el símbolo de intercalación dentro de la clase y especifique el método que se invalide.  
  
     Por ejemplo, escriba `public override` para ver una lista de todos los métodos que se pueden invalidar en esa clase.  
  
## <a name="see-also"></a>Vea también  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)

