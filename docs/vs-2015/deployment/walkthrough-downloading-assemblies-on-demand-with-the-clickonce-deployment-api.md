---
title: 'Tutorial: descargar ensamblados a petición con la API de implementación de ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af03329a05501427f6d04d6cddbd637c3311b339
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842762"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Tutorial: Descargar ensamblados a petición con la API de implementación de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De forma predeterminada, todos los ensamblados incluidos en una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación se descargan cuando se ejecuta la aplicación por primera vez. Sin embargo, puede tener partes de la aplicación que se usan en un pequeño conjunto de usuarios. En tal caso, es probable que quiera descargar un ensamblado solo cuando cree uno de sus tipos. En el siguiente tutorial se muestra cómo marcar determinados ensamblados en la aplicación como “opcionales” y cómo descargarlos usando clases en el espacio de nombres <xref:System.Deployment.Application> cuando los solicita Common Language Runtime (CLR).  
  
> [!NOTE]
> La aplicación deberá ejecutarse con plena confianza para poder usar este procedimiento.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, necesitará uno de los siguientes componentes:  
  
- Windows SDK. El Windows SDK se puede descargar desde el centro de descarga de Microsoft.  
  
- Visual Studio.  
  
## <a name="creating-the-projects"></a>Crear los proyectos  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Para crear un proyecto que use un ensamblado a petición  
  
1. Cree un directorio denominado ClickOnceOnDemand.  
  
2. Abra el símbolo del sistema de Windows SDK o el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] símbolo del sistema.  
  
3. Cambie al directorio ClickOnceOnDemand.  
  
4. Genere un par de claves pública y privada con el siguiente comando:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5. Con el Bloc de notas u otro editor de texto, defina una clase denominada `DynamicClass` con una sola propiedad denominada `Message` .  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6. Guarde el texto como un archivo denominado `ClickOnceLibrary.cs` o `ClickOnceLibrary.vb` , en función del idioma que use, en el directorio ClickOnceOnDemand.  
  
7. Compile el archivo en un ensamblado.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8. Para obtener el token de clave pública para el ensamblado, use el siguiente comando:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Cree un nuevo archivo con el editor de texto y escriba el código siguiente. Este código crea una aplicación Windows Forms que descarga el ensamblado ClickOnceLibrary cuando es necesario.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. En el código, busque la llamada a <xref:System.Reflection.Assembly.LoadFile%2A> .  
  
11. Establezca `PublicKeyToken` en el valor que recuperó anteriormente.  
  
12. Guarde el archivo como `Form1.cs` o `Form1.vb` .  
  
13. Compílelo en un archivo ejecutable mediante el siguiente comando.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Marcar ensamblados como opcionales  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Para marcar los ensamblados como opcionales en la aplicación ClickOnce mediante MageUI.exe  
  
1. Con MageUI.exe, cree un manifiesto de aplicación tal como se describe en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Use la siguiente configuración para el manifiesto de aplicación:  
  
    - Asigne al manifiesto de aplicación el nombre `ClickOnceOnDemand` .  
  
    - En la página **archivos** , en la fila ClickOnceLibrary.dll, establezca la columna **tipo de archivo** en **ninguno**.  
  
    - En la página **archivos** , en la fila ClickOnceLibrary.dll, escriba `ClickOnceLibrary.dll` en la columna **Grupo** .  
  
2. Con MageUI.exe, cree un manifiesto de implementación como se describe en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Use la siguiente configuración para el manifiesto de implementación:  
  
    - Nombre el manifiesto de implementación `ClickOnceOnDemand` .  
  
## <a name="testing-the-new-assembly"></a>Probar el nuevo ensamblado  
  
#### <a name="to-test-your-on-demand-assembly"></a>Para probar el ensamblado a petición  
  
1. Cargue la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación en un servidor Web.  
  
2. Inicie la aplicación implementada con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] desde un explorador Web. para ello, escriba la dirección URL del manifiesto de implementación. Si llama a la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación `ClickOnceOnDemand` y la carga en el directorio raíz de Adatum.com, la dirección URL tendría el siguiente aspecto:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3. Cuando aparezca el formulario principal, pulse el <xref:System.Windows.Forms.Button>. Debería ver una cadena en una ventana de cuadro de mensaje que dice “Hello, World!”.  
  
## <a name="see-also"></a>Consulte también  
 <xref:System.Deployment.Application.ApplicationDeployment>
