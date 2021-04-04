---
title: 'Tutorial: crear un servicio de lenguaje heredado | Microsoft Docs'
description: Obtenga información sobre cómo usar las clases de lenguaje de Managed Package Framework para implementar un servicio de lenguaje en Visual C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42c9f2d2a91b90cab31dd225d0ace081988135fb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213646"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Tutorial: Creación de un servicio de lenguaje heredado
El uso de las clases de lenguaje de Managed Package Framework (MPF) para implementar un servicio de lenguaje en [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] es sencillo. Necesita un VSPackage para hospedar el servicio de lenguaje, el propio servicio de lenguaje y un analizador para su lenguaje.

## <a name="prerequisites"></a>Prerrequisitos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Ubicaciones de la plantilla de proyecto de paquete de Visual Studio
 La plantilla de proyecto de paquete de Visual Studio puede encontrarse en tres ubicaciones de plantillas diferentes en el cuadro de diálogo **nuevo proyecto** :

1. En Extensibilidad de Visual Basic. El lenguaje predeterminado del proyecto es Visual Basic.

2. En Extensibilidad de C#. El lenguaje predeterminado del proyecto es C#.

3. En otro tipos de extensibilidad del proyecto. El lenguaje predeterminado del proyecto es C++.

### <a name="create-a-vspackage"></a>Crear un VSPackage

1. Cree un nuevo VSPackage con la plantilla de proyecto de paquete de Visual Studio.

    Si va a agregar un servicio de lenguaje a un VSPackage existente, omita los pasos siguientes y vaya directamente al procedimiento "crear la clase de servicio de lenguaje".

2. Escriba MyLanguagePackage para el nombre del proyecto y haga clic en **Aceptar**.

    Puede usar cualquier nombre que desee. Estos procedimientos detallados aquí suponen MyLanguagePackage como nombre.

3. Seleccione [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] como lenguaje y la opción para generar un nuevo archivo de clave. Haga clic en **Next**.

4. Escriba la información de la compañía y del paquete adecuada. Haga clic en **Next**.

5. Seleccione el **comando de menú**. Haga clic en **Next**.

    Si no tiene previsto admitir fragmentos de código, puede hacer clic en finalizar y omitir el paso siguiente.

6. Escriba **Insertar fragmento de código** como el **nombre del comando** y `cmdidInsertSnippet` para el **identificador de comando**. Haga clic en **Finalizar**

    El **nombre de comando** y el ID. de **comando** pueden ser el que desee, es decir, solo ejemplos.

### <a name="create-the-language-service-class"></a>Crear la clase de servicio de lenguaje

1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto MyLanguagePackage, elija **Agregar**, **referencia** y, a continuación, elija el botón **Agregar nueva referencia** .

2. En el cuadro de diálogo **Agregar referencia** , seleccione **Microsoft. VisualStudio. Package. LanguageService** en la pestaña **.net** y haga clic en **Aceptar**.

     Esto debe hacerse solo una vez para el proyecto de paquete de idioma.

3. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto VSPackage y seleccione **Agregar**, **clase**.

4. Asegúrese de que la **clase** está seleccionada en la lista de plantillas.

5. Escriba **MyLanguageService. CS** como nombre del archivo de clase y haga clic en **Agregar**.

     Puede usar cualquier nombre que desee. Estos procedimientos detallados aquí suponen `MyLanguageService` como nombre.

6. En el archivo MyLanguageService. CS, agregue las siguientes `using` directivas.

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs" id="Snippet1":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb" id="Snippet1":::

7. Modifique la `MyLanguageService` clase para que derive de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase:

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs" id="Snippet2":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb" id="Snippet2":::

8. Coloque el cursor en "LanguageService" y, en el menú **Editar**, **IntelliSense** , seleccione **implementar clase abstracta**. Esto agrega los métodos necesarios mínimos para implementar una clase de servicio de lenguaje.

9. Implemente los métodos abstractos tal y como se describe en [implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Registrar el servicio de lenguaje

1. Abra el archivo MyLanguagePackagePackage. CS y agregue las siguientes `using` directivas:

     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguagepackagepackage.vb" id="Snippet3":::
     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguagepackagepackage.cs" id="Snippet3":::

2. Registre la clase del servicio de lenguaje tal y como se describe en [registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md). Esto incluye los atributos ProvideXX y las secciones "Proffering The Language Service". Use MyLanguageService donde este tema usa TestLanguageService.

### <a name="the-parser-and-scanner"></a>Analizador y escáner

1. Implemente un analizador y un escáner para su idioma, tal y como se describe en [analizador y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     La forma en que se implementa el analizador y el analizador es totalmente suya y está fuera del ámbito de este tema.

## <a name="language-service-features"></a>Características del servicio de lenguaje
 Para implementar cada característica en el servicio de lenguaje, normalmente se deriva una clase de la clase de servicio de lenguaje MPF adecuada, se implementan todos los métodos abstractos según sea necesario y se invalidan los métodos adecuados. Las clases que se crean o se derivan de dependen de las características que se van a admitir. Estas características se describen en detalle en [características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md). El procedimiento siguiente es el enfoque general para derivar una clase de las clases MPF.

#### <a name="deriving-from-an-mpf-class"></a>Derivación de una clase MPF

1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto VSPackage y seleccione **Agregar**, **clase**.

2. Asegúrese de que la **clase** está seleccionada en la lista de plantillas.

     Escriba un nombre adecuado para el archivo de clase y haga clic en **Agregar**.

3. En el nuevo archivo de clase, agregue las siguientes `using` directivas.

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs" id="Snippet4":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb" id="Snippet4":::

4. Modifique la clase para que se derive de la clase MPF deseada.

5. Agregue un constructor de clase que tome al menos los mismos parámetros que el constructor de la clase base y pase los parámetros de constructor en al constructor de clase base.

     Por ejemplo, el constructor para una clase derivada de la <xref:Microsoft.VisualStudio.Package.Source> clase podría tener un aspecto similar al siguiente:

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs" id="Snippet5":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb" id="Snippet5":::

6. En el menú **Editar**, **IntelliSense** , seleccione **implementar clase abstracta** si la clase base tiene algún método abstracto que se deba implementar.

7. De lo contrario, coloque el símbolo de intercalación dentro de la clase y escriba el método que se va a invalidar.

     Por ejemplo, escriba `public override` para ver una lista de todos los métodos que se pueden invalidar en esa clase.

## <a name="see-also"></a>Consulte también
- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
