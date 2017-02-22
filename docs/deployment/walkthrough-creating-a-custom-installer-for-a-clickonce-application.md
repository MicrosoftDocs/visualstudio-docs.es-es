---
title: "Tutorial: Crear un instalador personalizado para una aplicaci&#243;n ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "implementación ClickOnce, instalador personalizado"
  - "instalador personalizado [ClickOnce]"
  - "implementar aplicaciones [ClickOnce], instalador personalizado"
  - "InPlaceHostingManager [ClickOnce], instalador personalizado"
  - "instalador [ClickOnce], personalizado"
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tutorial: Crear un instalador personalizado para una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cualquier aplicación ClickOnce basada en un archivo .exe se puede instalar y actualizar silenciosamente mediante un instalador personalizado.  Un instalador personalizado puede implementar una experiencia del usuario personalizada durante la instalación, incluidos cuadros de diálogo personalizados de seguridad y operaciones de mantenimiento.  Para realizar las operaciones de instalación, el instalador personalizado utiliza la clase <xref:System.Deployment.Application.InPlaceHostingManager>.  Este tutorial muestra cómo crear un instalador personalizado que instala silenciosamente una aplicación ClickOnce.  
  
## Requisitos previos  
  
### Para crear un instalador de aplicación ClickOnce personalizado  
  
1.  En la aplicación ClickOnce, agregue referencias a System.Deployment y System.Windows.Forms.  
  
2.  Agregue una nueva clase a la aplicación y especifique cualquier nombre.  En este tutorial se utiliza el nombre `MyInstaller`.  
  
3.  Agregue las siguientes instrucciones `Imports` o `using` al principio de la nueva clase.  
  
    ```vb#  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```c#  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Agregue los métodos siguientes a la clase.  
  
     Estos métodos llaman a métodos de <xref:System.Deployment.Application.InPlaceHostingManager> para descargar el manifiesto de implementación, validar los permisos adecuados, pedir al usuario permiso para instalar y, por último, descargar e instalar la aplicación en la memoria caché de ClickOnce.  Un instalador personalizado puede especificar previamente que una aplicación ClickOnce sea de confianza, o bien diferir la decisión de confianza hasta la llamada al método <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>.  Este código especifica previamente que la aplicación es de confianza.  
  
    > [!NOTE]
    >  Los permisos asignados por la especificación de confianza previa no pueden superar los permisos del código del instalador personalizado.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-cs[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Para intentar la instalación desde el código, llame al método `InstallApplication`.  Por ejemplo, si la clase se llama `MyInstaller`, se puede llamar a `InstallApplication` de la siguiente manera.  
  
    ```vb#  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```c#  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
  
    ```  
  
## Pasos siguientes  
 Una aplicación ClickOnce también puede agregar lógica de actualizaciones personalizada, incluso una interfaz de usuario personalizada que se muestre durante el proceso de actualización.  Para obtener más información, vea <xref:System.Deployment.Application.UpdateCheckInfo>.  Una aplicación ClickOnce también puede suprimir la entrada estándar del menú Inicio, el acceso directo y la entrada de Agregar o quitar programas, mediante un elemento `<customUX>`.  Para obtener más información, vea [\<entryPoint\> \(Elemento\)](../deployment/entrypoint-element-clickonce-application.md) y <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint\> \(Elemento\)](../deployment/entrypoint-element-clickonce-application.md)