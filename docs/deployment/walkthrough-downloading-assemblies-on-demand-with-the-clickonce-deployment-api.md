---
title: 'Tutorial: Descargar ensamblados a petición con la API de implementación ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: cadba0d6afd35303fd44eb0442bb8f4eb9aa8440
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603904"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Tutorial: Descargar ensamblados a petición con la API de implementación de ClickOnce
De forma predeterminada, todos los ensamblados incluyen en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se descargan cuando la aplicación se ejecuta en primer lugar. Sin embargo, puede tener partes de la aplicación que usan un conjunto pequeño de los usuarios. En tal caso, es probable que quiera descargar un ensamblado solo cuando cree uno de sus tipos. En el siguiente tutorial se muestra cómo marcar determinados ensamblados en la aplicación como “opcionales” y cómo descargarlos usando clases en el espacio de nombres <xref:System.Deployment.Application> cuando los solicita Common Language Runtime (CLR).

> [!NOTE]
>  La aplicación deberá ejecutarse con plena confianza para poder usar este procedimiento.

## <a name="prerequisites"></a>Requisitos previos
 Necesitará uno de los componentes siguientes para completar este tutorial:

-   El SDK de Windows. El SDK de Windows puede descargarse desde Microsoft Download Center.

-   Visual Studio.

## <a name="create-the-projects"></a>Crear los proyectos

#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Para crear un proyecto que usa un ensamblado y a petición

1. Cree un directorio denominado ClickOnceOnDemand.

2. Abra el símbolo del sistema de Windows SDK o la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] símbolo del sistema.

3. Cambie al directorio ClickOnceOnDemand.

4. Generar un par de claves pública y privada con el comando siguiente:

   ```cmd
   sn -k TestKey.snk
   ```

5. Con el Bloc de notas u otro editor de texto, definir una clase denominada `DynamicClass` con una propiedad única denominada `Message`.

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]

6. Guarde el texto como un archivo denominado *ClickOnceLibrary.cs* o *ClickOnceLibrary.vb*, según el lenguaje que use, a la *ClickOnceOnDemand* directory.

7. Compile el archivo en un ensamblado.

   ```csharp
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs
   ```

   ```vb
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb
   ```

8. Para obtener la clave pública token para el ensamblado, use el comando siguiente:

   ```cmd
   sn -T ClickOnceLibrary.dll
   ```

9. Crear un nuevo archivo con el texto del editor y escriba el código siguiente. Este código crea una aplicación de Windows Forms que descarga el ensamblado ClickOnceLibrary cuando sea necesario.

     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]

10. En el código, busque la llamada a <xref:System.Reflection.Assembly.LoadFile%2A>.

11. Establecer`PublicKeyToken` en el valor que recuperó anteriormente.

12. Guarde el archivo como *Form1.cs* o *Form1.vb*.

13. Compila en una aplicación ejecutable mediante el siguiente comando.

    ```csharp
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs
    ```

    ```vb
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb
    ```

## <a name="mark-assemblies-as-optional"></a>Marque los ensamblados como opcionales

#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Para marcar ensamblados como opcionales en la aplicación ClickOnce con MageUI.exe

1.  Uso de *MageUI.exe*, cree un manifiesto de aplicación como se describe en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Utilice la siguiente configuración para el manifiesto de aplicación:

    -   Nombre del manifiesto de aplicación `ClickOnceOnDemand`.

    -   En el **archivos** página, en el *ClickOnceLibrary.dll* de fila, establezca el **tipo de archivo** columna **ninguno**.

    -   En el **archivos** página, en el *ClickOnceLibrary.dll* , escriba `ClickOnceLibrary.dll` en el **grupo** columna.

2.  Uso de *MageUI.exe*, cree un manifiesto de implementación como se describe en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Utilice la siguiente configuración para el manifiesto de implementación:

    -   Nombre del manifiesto de implementación `ClickOnceOnDemand`.

## <a name="testing-the-new-assembly"></a>Probar el nuevo ensamblado

#### <a name="to-test-your-on-demand-assembly"></a>Para probar el ensamblado a petición

1. Cargue su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación en un servidor Web.

2. Inicie la aplicación implementada con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] desde un explorador Web escribiendo la dirección URL para el manifiesto de implementación. Si se llama a su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación `ClickOnceOnDemand`y cargarlo en el directorio raíz de adatum.com, la dirección URL tendría el aspecto siguiente:

   ```
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application
   ```

3. Cuando aparezca el formulario principal, pulse el <xref:System.Windows.Forms.Button>. Debería ver una cadena en una ventana de cuadro de mensaje que dice “Hello, World!”.

## <a name="see-also"></a>Vea también
- <xref:System.Deployment.Application.ApplicationDeployment>