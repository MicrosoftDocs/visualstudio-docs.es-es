---
title: "C&#243;mo: Permitir que el c&#243;digo se ejecute en documentos con permisos restringidos"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "código [desarrollo de Office en Visual Studio], ejecutar en documentos con permisos restringidos"
  - "documentos [desarrollo de Office en Visual Studio], permisos restringidos"
  - "Information Rights Management [desarrollo de Office en Visual Studio]"
  - "IRM [desarrollo de Office en Visual Studio]"
  - "documentos de Office [desarrollo de Office en Visual Studio], permisos restringidos"
  - "permisos [desarrollo de Office en Visual Studio]"
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# C&#243;mo: Permitir que el c&#243;digo se ejecute en documentos con permisos restringidos
  Puede utilizar la característica Information Rights Management \(IRM\) de Microsoft Office para restringir los permisos a un documento o libro.  De forma predeterminada, no está permitido ejecutar el código subyacente de un documento Microsoft Office Word o de un libro de Microsoft Office Excel restringidos.  Puede cambiar el valor predeterminado para que las extensiones de código administrado puedan tener acceso al modelo de objetos y para que funcione la solución.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Debe ser el autor del documento o del libro, o tener control total para poder cambiar la configuración de permisos.  
  
### Para permitir que el código se ejecute en documentos con permisos restringidos  
  
1.  Abra el documento o el libro en Word o Excel.  
  
2.  Haga clic en la pestaña **Archivo** , elija **Preparación**, elija **Limite el permiso**, y haga clic en **Acceso restringido**.  
  
    > [!NOTE]  
    >  La primera vez que lo use, se le pedirá que instale el cliente de Windows Rights Management.  Es posible que después de instalar el cliente tenga que repetir los pasos.  
  
3.  En el cuadro de diálogo **Permiso**, seleccione **Restringir permisos para este documento** y, a continuación, haga clic en **Más opciones**.  
  
4.  Debajo de **Permisos adicionales para los usuarios**, seleccione **Obtener acceso al contenido mediante programación**.  
  
 Word o Excel permitirán el acceso mediante programación al modelo de objetos.  
  
## Vea también  
 [Información general sobre la administración de permisos sobre la información y las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  