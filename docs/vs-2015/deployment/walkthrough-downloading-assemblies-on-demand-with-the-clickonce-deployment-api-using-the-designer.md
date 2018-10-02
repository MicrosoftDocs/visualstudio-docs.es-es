---
title: 'Tutorial: Descargar ensamblados a petición con la implementación de ClickOnce mediante el Diseñador de API | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 827f524a5038c57283f33e519f3df972dbf72b26
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581656"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Tutorial: Descargar ensamblados a petición con la API de implementación de ClickOnce mediante el diseñador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Tutorial: descargar ensamblados a petición con la implementación de ClickOnce API mediante el diseñador](https://docs.microsoft.com/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).  
  
De forma predeterminada, todos los ensamblados incluidos en una aplicación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se descargan la primera vez que se ejecuta la aplicación, aunque podría haber partes de la aplicación usadas por un pequeño sector de los usuarios. En tal caso, es probable que quiera descargar un ensamblado solo cuando cree uno de sus tipos. En el siguiente tutorial se muestra cómo marcar determinados ensamblados en la aplicación como “opcionales” y cómo descargarlos usando clases en el espacio de nombres <xref:System.Deployment.Application> cuando los solicita Common Language Runtime.  
  
> [!NOTE]
>  La aplicación deberá ejecutarse con plena confianza para poder usar este procedimiento.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, haga clic en **Importar y exportar configuraciones** en el menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-projects"></a>Crear los proyectos  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Para crear un proyecto que use un ensamblado a petición con Visual Studio  
  
1.  Cree un proyecto de Windows Forms en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. En el menú **Archivo** , apunte a **Agregar**y haga clic en **Nuevo proyecto**. Elija un proyecto **Biblioteca de clases** en el cuadro de diálogo y asígnele el nombre `ClickOnceLibrary`.  
  
    > [!NOTE]
    >  En Visual Basic, se recomienda modificar las propiedades del proyecto para cambiar el espacio de nombres raíz de este proyecto a `Microsoft.Samples.ClickOnceOnDemand` o al espacio de nombres que quiera. Para que resulte más sencillo, los dos proyectos de este tutorial están en el mismo espacio de nombres.  
  
2.  Defina una clase denominada `DynamicClass` con una propiedad única denominada `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
3.  Seleccione el proyecto de Windows Forms en el **Explorador de soluciones**. Agregue una referencia al ensamblado <xref:System.Deployment.Application> y una referencia de proyecto al proyecto `ClickOnceLibrary` .  
  
    > [!NOTE]
    >  En Visual Basic, se recomienda modificar las propiedades del proyecto para cambiar el espacio de nombres raíz de este proyecto a `Microsoft.Samples.ClickOnceOnDemand` o al espacio de nombres que quiera. Para que resulte más sencillo, los dos proyectos de este tutorial están ubicados en el mismo espacio de nombres.  
  
4.  Haga clic con el botón derecho en el formulario, haga clic en **Ver código** en el menú y agregue las siguientes referencias al formulario.  
  
     [!code-csharp[ClickOnceOnDemand#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemand#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#1)]  
  
5.  Agregue el siguiente código para descargar este ensamblado a petición. En este código se muestra cómo asignar un conjunto de ensamblados a un nombre de grupo con una clase <xref:System.Collections.DictionaryBase.Dictionary%2A> genérica. Dado que en este tutorial solo vamos a descargar un ensamblado, solo hay un ensamblado en nuestro grupo. En una aplicación real, probablemente querría descargar en la aplicación todos los ensamblados relacionados con una característica al mismo tiempo. La tabla de asignación le permite hacer esto fácilmente asociando todos los archivos DLL de una característica con un nombre de grupo de descarga.  
  
     [!code-csharp[ClickOnceOnDemand#2](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#2)]
     [!code-vb[ClickOnceOnDemand#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#2)]  
  
6.  En el menú **Ver** , haga clic en **Cuadro de herramientas**. Arrastre un <xref:System.Windows.Forms.Button> del **Cuadro de herramientas** al formulario. Haga doble clic en el botón y agregue el siguiente código al controlador de eventos <xref:System.Windows.Forms.Control.Click> .  
  
     [!code-csharp[ClickOnceOnDemand#3](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#3)]
     [!code-vb[ClickOnceOnDemand#3](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#3)]  
  
## <a name="marking-assemblies-as-optional"></a>Marcar ensamblados como opcionales  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Para marcar ensamblados como opcionales en la aplicación ClickOnce con Visual Studio  
  
1.  Haga clic con el botón derecho en el proyecto de Windows Forms en el **Explorador de soluciones** y haga clic en **Propiedades**. Seleccione la pestaña **Publicar** .  
  
2.  Haga clic en el botón **Archivos de aplicación** .  
  
3.  Busque la lista de ClickOnceLibrary.dll. Establezca el cuadro desplegable **Estado de publicación** en **Incluir**.  
  
4.  Expanda el cuadro desplegable **Grupo** y seleccione **Nuevo**. Escriba el nombre `ClickOnceLibrary` como nuevo nombre del grupo.  
  
5.  Siga publicando la aplicación como se describe en [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Para marcar ensamblados como opcionales en la aplicación ClickOnce con la Herramienta de generación y edición de manifiestos: cliente gráfico (MageUI.exe)  
  
1.  Cree su [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se manifiesta como se describe en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Antes de cerrar MageUI.exe, seleccione la pestaña que contiene el manifiesto de aplicación de su implementación y, en esa pestaña, seleccione la pestaña **Archivos** .  
  
3.  Busque ClickOnceLibrary.dll en la lista de archivos de la aplicación y establezca la columna **Tipo de archivo** en **Ninguno**. En la columna **Grupo** , escriba `ClickOnceLibrary.dll`.  
  
## <a name="testing-the-new-assembly"></a>Probar el nuevo ensamblado  
  
#### <a name="to-test-your-on-demand-assembly"></a>Para probar el ensamblado a petición  
  
1.  Inicie la aplicación implementada con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2.  Cuando aparezca el formulario principal, pulse el <xref:System.Windows.Forms.Button>. Debería ver una cadena en una ventana de cuadro de mensaje que dice “Hello, World!”.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Deployment.Application.ApplicationDeployment>



