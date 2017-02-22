---
title: "Tutorial: Descargar ensamblados a petici&#243;n con la API de implementaci&#243;n de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ensamblados, descargar [ClickOnce]"
  - "implementación ClickOnce, descarga a petición"
  - "ensamblados a petición, ClickOnce"
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tutorial: Descargar ensamblados a petici&#243;n con la API de implementaci&#243;n de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

De forma predeterminada, todos los ensamblados incluidos en una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se descargan la primera vez que se ejecuta la aplicación.  Sin embargo, puede que un pequeño conjunto de usuarios utilice algunos componentes de la aplicación.  En este caso, sólo descargará un ensamblado cuando cree uno de los tipos.  En el tutorial siguiente se muestra cómo marcar determinados ensamblados de la aplicación como "opcional" y cómo descargarlos utilizando clases del espacio de nombres <xref:System.Deployment.Application> cuando Common Language Runtime \(CLR\) los solicite.  
  
> [!NOTE]
>  Para poder utilizar este procedimiento, es necesario que la aplicación se ejecute con plena confianza.  
  
## Requisitos previos  
 Necesitará uno de los componentes siguientes para completar este tutorial:  
  
-   SDK de Windows.  El SDK de Windows se puede descargar desde el Centro de descarga de Microsoft.  
  
-   Visual Studio.  
  
## Crear los proyectos  
  
#### Para crear un proyecto que utilice un ensamblado a petición  
  
1.  Cree un directorio denominado ClickOnceOnDemand.  
  
2.  Abra el símbolo del sistema del SDK de Windows o de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Cambie al directorio ClickOnceOnDemand.  
  
4.  Cree un par de claves pública y privada con el comando siguiente:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Con el Bloc de notas u otro editor de texto, defina una clase denominada `DynamicClass` con una propiedad única denominada `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-cs[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Guarde el texto como un archivo denominado `ClickOnceLibrary.cs` o `ClickOnceLibrary.vb`, en función del lenguaje que utilice, en el directorio ClickOnceOnDemand.  
  
7.  Compile el archivo en un ensamblado.  
  
    ```c#  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb#  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Para obtener el token de clave pública del ensamblado, utilice el comando siguiente:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Cree un nuevo archivo mediante el editor de texto y escriba el código siguiente.  Este código crea una aplicación de formularios Windows Forms que descarga el ensamblado ClickOnceLibrary cuando así se requiere.  
  
     [!code-cs[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. En el código, busque la llamada a <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Establezca `PublicKeyToken` en el valor que recuperó anteriormente.  
  
12. Guarde el archivo como `Form1.cs` o `Form1.vb`.  
  
13. Compílelo en un ejecutable mediante el comando siguiente.  
  
    ```c#  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb#  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## Marcar los ensamblados como opcional  
  
#### Para marcar los ensamblados como opcionales en la aplicación ClickOnce utilizando MageUI.exe  
  
1.  Con MageUI.exe, cree un manifiesto de aplicación, tal y como se describe en [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Utilice la configuración siguiente para el manifiesto de aplicación:  
  
    -   Llame al manifiesto de la aplicación `ClickOnceOnDemand`.  
  
    -   En la página **Archivos**, en la fila de ClickOnceLibrary.dll, establezca la columna **Tipo de archivo** en **Ninguno**.  
  
    -   En la página **Archivos**, en la fila de ClickOnceLibrary.dll, escriba `ClickOnceLibrary.dll` en la columna **Grupo**.  
  
2.  Utilizando MageUI.exe, cree un manifiesto de implementación, tal y como se describe en [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Utilice la configuración siguiente para el manifiesto de implementación:  
  
    -   Llame `ClickOnceOnDemand` al manifiesto de implementación.  
  
## Probar el nuevo ensamblado  
  
#### Para probar el ensamblado a petición  
  
1.  Cargue la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en un servidor web.  
  
2.  Inicie la aplicación implementada con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] desde un explorador web; para ello, escriba la dirección URL del manifiesto de implementación.  Si llama a la aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `ClickOnceOnDemand` y la carga en el directorio raíz de adatum.com, la dirección URL presentará el siguiente aspecto:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Cuando aparezca el formulario principal, presione <xref:System.Windows.Forms.Button>.  Verá una cadena en una ventana de cuadro de mensaje con el texto, "Hello, World\!".  
  
## Vea también  
 <xref:System.Deployment.Application.ApplicationDeployment>