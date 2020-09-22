---
title: Descargar ensamblados a petición (API de ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8452bec3443b93737e4799a8f09c8e342f011976
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809255"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Tutorial: descargar ensamblados a petición con la API de implementación de ClickOnce
De forma predeterminada, todos los ensamblados incluidos en una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se descargan cuando se ejecuta la aplicación por primera vez. Sin embargo, puede tener partes de la aplicación que se usan en un pequeño conjunto de usuarios. En tal caso, es probable que quiera descargar un ensamblado solo cuando cree uno de sus tipos. En el siguiente tutorial se muestra cómo marcar determinados ensamblados en la aplicación como “opcionales” y cómo descargarlos usando clases en el espacio de nombres <xref:System.Deployment.Application> cuando los solicita Common Language Runtime (CLR).

> [!NOTE]
> La aplicación deberá ejecutarse con plena confianza para poder usar este procedimiento.

## <a name="prerequisites"></a>Requisitos previos
 Para completar este tutorial, necesitará uno de los siguientes componentes:

- Windows SDK. El Windows SDK se puede descargar desde el centro de descarga de Microsoft.

- Visual Studio.

## <a name="create-the-projects"></a>Crear los proyectos

#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Para crear un proyecto que use un ensamblado a petición

1. Cree un directorio denominado ClickOnceOnDemand.

2. Abra el símbolo del sistema de Windows SDK o el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] símbolo del sistema.

3. Cambie al directorio ClickOnceOnDemand.

4. Genere un par de claves pública y privada con el siguiente comando:

   ```cmd
   sn -k TestKey.snk
   ```

5. Con el Bloc de notas u otro editor de texto, defina una clase denominada `DynamicClass` con una sola propiedad denominada `Message` .

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]

6. Guarde el texto como un archivo denominado *ClickOnceLibrary.CS* o *ClickOnceLibrary. VB*, según el lenguaje que use, en el directorio *ClickOnceOnDemand* .

7. Compile el archivo en un ensamblado.

   ```csharp
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs
   ```

   ```vb
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb
   ```

8. Para obtener el token de clave pública para el ensamblado, use el siguiente comando:

   ```cmd
   sn -T ClickOnceLibrary.dll
   ```

9. Cree un nuevo archivo con el editor de texto y escriba el código siguiente. Este código crea una aplicación Windows Forms que descarga el ensamblado ClickOnceLibrary cuando es necesario.

     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]

10. En el código, busque la llamada a <xref:System.Reflection.Assembly.LoadFile%2A> .

11. Establezca `PublicKeyToken` en el valor que recuperó anteriormente.

12. Guarde el archivo como *Form1.CS* o *Form1. VB*.

13. Compílelo en un archivo ejecutable mediante el siguiente comando.

    ```csharp
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs
    ```

    ```vb
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb
    ```

## <a name="mark-assemblies-as-optional"></a>Marcar los ensamblados como opcionales

#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Para marcar los ensamblados como opcionales en la aplicación ClickOnce mediante MageUI.exe

1. Con *MageUI.exe*, cree un manifiesto de aplicación tal como se describe en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Use la siguiente configuración para el manifiesto de aplicación:

    - Asigne al manifiesto de aplicación el nombre `ClickOnceOnDemand` .

    - En la página **archivos** , en la fila *ClickOnceLibrary.dll* , establezca la columna **tipo de archivo** en **ninguno**.

    - En la página **archivos** , en la fila *ClickOnceLibrary.dll* , escriba `ClickOnceLibrary.dll` en la columna **Grupo** .

2. Con *MageUI.exe*, cree un manifiesto de implementación como se describe en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Use la siguiente configuración para el manifiesto de implementación:

    - Nombre el manifiesto de implementación `ClickOnceOnDemand` .

## <a name="testing-the-new-assembly"></a>Probar el nuevo ensamblado

#### <a name="to-test-your-on-demand-assembly"></a>Para probar el ensamblado a petición

1. Cargue la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación en un servidor Web.

2. Inicie la aplicación implementada con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] desde un explorador Web. para ello, escriba la dirección URL del manifiesto de implementación. Si llama a la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación `ClickOnceOnDemand` y la carga en el directorio raíz de Adatum.com, la dirección URL tendría el siguiente aspecto:

   ```
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application
   ```

3. Cuando aparezca el formulario principal, pulse el <xref:System.Windows.Forms.Button>. Debería ver una cadena en una ventana de cuadro de mensaje que dice “Hello, World!”.

## <a name="see-also"></a>Consulte también
- <xref:System.Deployment.Application.ApplicationDeployment>