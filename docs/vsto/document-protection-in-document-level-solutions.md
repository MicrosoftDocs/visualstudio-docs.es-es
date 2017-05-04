---
title: "Protecci&#243;n de documentos en soluciones de nivel de documento | Microsoft Docs"
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
  - "documentos [desarrollo de Office en Visual Studio], permisos restringidos"
  - "documentos de Office [desarrollo de Office en Visual Studio], permisos restringidos"
  - "permisos [desarrollo de Office en Visual Studio]"
  - "permisos restringidos [desarrollo de Office en Visual Studio]"
  - "libros [desarrollo de Office en Visual Studio], permisos restringidos"
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Protecci&#243;n de documentos en soluciones de nivel de documento
  En los proyectos de nivel de documento, se pueden usar las características de protección de Microsoft Office Word y Microsoft Office Excel.  Estas características impiden que los usuarios no autorizados puedan realizar cambios en las partes protegidas de los documentos.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Utilizando Excel, puede habilitar o deshabilitar la protección mientras el libro esté abierto en el diseñador.  Si utiliza Word, sólo puede activar la protección desde fuera del diseñador.  En tiempo de ejecución puede habilitar o deshabilitar la protección mediante programación, tanto para Word como para Excel.  
  
 Cuando la protección de documentos está habilitada en un documento que abierto en el diseñador, desaparecen todos los controles del **Cuadro de herramientas** o no están disponibles, ni tampoco se puede arrastrar ningún elemento desde la ventana **Orígenes de datos** hasta el documento.  
  
## ServerDocument y documentos protegidos  
 Si un documento está protegido, no se puede obtener acceso a la memoria caché de datos desde fuera del documento.  No se puede utilizar la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para recuperar ni manipular los datos almacenados en la memoria caché de un documento protegido, ni tampoco utilizar otros métodos de la clase <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>.  
  
## Protección de documentos de Word en el diseñador  
 Si agrega protección a un documento o plantilla de Word mientras está abierto en Visual Studio, no podrá habilitar la protección desde el diseñador.  El documento está en modo de diseño mientras está abierto en Visual Studio y debe encontrarse en modo de ejecución para habilitar la protección.  
  
 Sin embargo, si crea un proyecto que utilice un documento de Word existente que tenga la protección habilitada, el documento estará protegido mientras esté abierto en el diseñador.  No podrá modificar las partes protegidas del documento, pero sí podrá escribir código en el Editor de código para automatizar el documento.  Tampoco podrá compilar el proyecto si la protección está habilitada mientras el documento esté abierto en Visual Studio.  
  
 Para poder modificar el documento y compilar el proyecto puede desactivar la protección mientras el documento esté abierto en el diseñador.  No obstante, no puede desactivar la protección de la copia del diseñador mientras esté realizando la depuración; el documento que se abre durante la depuración es una copia independiente de la que está abierta en el diseñador \(la copia de resultado se almacena en el directorio \\bin, en caso de usar Visual Basic, y en el directorio \\bin\\debug si se utiliza C\#\).  
  
 Puede habilitar la protección en la copia del documento que se abre en el diseñador cerrando el proyecto en Visual Studio, abriendo la copia del documento situada en el directorio del proyecto y activando entonces la protección en el mismo.  
  
## Forzar la protección de documentos de Word al compilar  
 Visual Studio comienza a aplicar la protección de los documentos y plantillas de Word durante el proceso de compilación, de manera que la protección está habilitada cuando el documento se abre para la depuración.  El documento se protege con una contraseña en blanco.  
  
 Durante la compilación la protección está habilitada de forma que si hay código en el evento <xref:Microsoft.Office.Tools.Word.Document.Startup> del código que podría provocar excepciones o cambiar el comportamiento de la aplicación, este código pueda depurarse correctamente.  Si habilita la protección después de abrir el documento, no se podrá depurar ni comprobar el código de inicialización.  
  
## Establecer la contraseña  
 Visual Studio habilita automáticamente la protección, pero no proporciona ninguna contraseña de forma predeterminada.  Si desea que la protección del documento tenga una contraseña, debe agregarla antes de implementar la solución.  Agregar una contraseña le habilita para permitir a los usuarios autorizados quitar la protección del documento; sin contraseña, la protección no se puede quitar fácilmente.  Para obtener información detallada sobre cómo establecer una contraseña, vea la Ayuda de la aplicación de Office concreta.  
  
## Vea también  
 [Cómo: Proteger documentos y partes de documentos mediante programación](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Información general sobre la administración de permisos sobre la información y las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Cómo: Permitir que el código se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  