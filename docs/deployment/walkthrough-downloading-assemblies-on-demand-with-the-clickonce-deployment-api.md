---
title: "Tutorial: Descargar ensamblados a petición con la API de implementación de ClickOnce | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 640c0852a3745d11aae119e3c00e024b594d9132
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Tutorial: Descargar ensamblados a petición con la API de implementación de ClickOnce
De forma predeterminada, todos los ensamblados incluyen en una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se descargan cuando se ejecuta la aplicación por primera vez. Sin embargo, habrá partes de la aplicación que usan un pequeño conjunto de usuarios. En tal caso, es probable que quiera descargar un ensamblado solo cuando cree uno de sus tipos. El tutorial siguiente muestra cómo marcar determinados ensamblados de la aplicación como "opcionales" y cómo descargarlos utilizando clases en el <xref:System.Deployment.Application> espacio de nombres cuando common language runtime (CLR) los solicite.  
  
> [!NOTE]
>  La aplicación deberá ejecutarse con plena confianza para poder usar este procedimiento.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesitará uno de los componentes siguientes para completar este tutorial:  
  
-   El SDK de Windows. El SDK de Windows puede descargarse desde Microsoft Download Center.  
  
-   Visual Studio.  
  
## <a name="creating-the-projects"></a>Crear los proyectos  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Para crear un proyecto que usa un ensamblado a petición  
  
1.  Cree un directorio denominado ClickOnceOnDemand.  
  
2.  Abra el símbolo del sistema de Windows SDK o la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] símbolo del sistema.  
  
3.  Cambie al directorio ClickOnceOnDemand.  
  
4.  Generar un par de claves pública/privada mediante el siguiente comando:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Con el Bloc de notas u otro editor de texto, defina una clase llamada `DynamicClass` con una propiedad única denominada `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Guarde el texto como un archivo denominado `ClickOnceLibrary.cs` o `ClickOnceLibrary.vb`, dependiendo del lenguaje que utilice, en el directorio ClickOnceOnDemand.  
  
7.  Compile el archivo en un ensamblado.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Para obtener el token la clave pública para el ensamblado, utilice el siguiente comando:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Cree un nuevo archivo con el texto de editor y escriba el código siguiente. Este código crea una aplicación de Windows Forms que descarga el ensamblado ClickOnceLibrary cuando sea necesario.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. En el código, busque la llamada a <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Establecer`PublicKeyToken` en el valor que recuperó anteriormente.  
  
12. Guarde el archivo como `Form1.cs` o `Form1.vb`.  
  
13. Compila en una aplicación ejecutable mediante el siguiente comando.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Marcar ensamblados como opcionales  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Para marcar los ensamblados como opcionales en la aplicación ClickOnce mediante MageUI.exe  
  
1.  Con MageUI.exe, cree un manifiesto de aplicación como se describe en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Utilice la siguiente configuración para el manifiesto de aplicación:  
  
    -   Nombre del manifiesto de aplicación `ClickOnceOnDemand`.  
  
    -   En el **archivos** página, en la fila de ClickOnceLibrary.dll, establezca la **tipo de archivo** columna **ninguno**.  
  
    -   En el **archivos** página, en el tipo de la fila ClickOnceLibrary.dll `ClickOnceLibrary.dll` en el **grupo** columna.  
  
2.  Con MageUI.exe, cree un manifiesto de implementación tal y como se describe en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Utilice la siguiente configuración para el manifiesto de implementación:  
  
    -   Nombre del manifiesto de implementación `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Probar el nuevo ensamblado  
  
#### <a name="to-test-your-on-demand-assembly"></a>Para probar el ensamblado a petición  
  
1.  Cargar su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación en un servidor Web.  
  
2.  Inicie la aplicación implementada con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] desde un explorador Web escribiendo la dirección URL y el manifiesto de implementación. Si se llama a su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación `ClickOnceOnDemand`y lo carga en el directorio raíz de adatum.com, la dirección URL sería similar al siguiente:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Cuando aparezca el formulario principal, pulse el <xref:System.Windows.Forms.Button>. Debería ver una cadena en una ventana de cuadro de mensaje que dice "Hello, World!".  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Deployment.Application.ApplicationDeployment>