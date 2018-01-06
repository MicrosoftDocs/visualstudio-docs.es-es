---
title: "Protección en soluciones de nivel de documento de documentos | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cb0ccb9369c3430cf04e7e7c6b62335721e8005f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="document-protection-in-document-level-solutions"></a>Protección de documentos en soluciones de nivel de documento
  Puede usar las características de protección de Microsoft Office Word y Microsoft Office Excel en proyectos de nivel de documento. Estas características impiden que los usuarios no autorizados puedan realizar cambios en los elementos protegidos de un documento.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Utiliza Excel, puede activar y desactivar la protección mientras el libro está abierto en el diseñador. Con Word, puede activar protección sólo fuera del diseñador. En tiempo de ejecución, puede habilitar o deshabilitar la protección mediante programación de Word y Excel.  
  
 Cuando se habilita la protección de documentos en un documento que esté abierto en el diseñador, se quitan todos los controles de la **cuadro de herramientas** o dejan de estar disponibles, y no se puede arrastrar cualquier cosa, desde el **orígenes de datos** ventana para el documento.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument y documentos protegidos  
 Si un documento está protegido, la caché de datos no se puede tener acceso desde fuera del documento. No se puede utilizar el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase para recuperar o manipular los datos que se almacena en caché en un documento protegido, o usar otros métodos de la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> clase.  
  
## <a name="word-document-protection-in-the-designer"></a>Protección de documentos de Word en el diseñador  
 Si agrega protección a una plantilla o un documento de Word mientras está abierto en Visual Studio, no se puede empezar a aplicar la protección en el diseñador. El documento está en modo de diseño mientras está abierto en Visual Studio y se debe estar en modo de ejecución para poder empezar a aplicar la protección.  
  
 Sin embargo, si crea un proyecto que usa un documento de Word existente que tiene habilitada la protección, el documento está protegido mientras está abierto en el diseñador. No se puede editar las partes del documento protegidas, pero todavía puede escribir código en el Editor de código para automatizar el documento. También se no se puede compilar el proyecto si la protección está habilitada mientras el documento está abierto en Visual Studio.  
  
 Puede desactivar protección mientras el documento está abierto en el diseñador para que pueda modificar el documento y compile el proyecto. No se puede desactivar la protección para la copia en el diseñador mientras está depurando; el documento que se abre durante la depuración es una copia independiente de la que está abierta en el diseñador (la copia de salida se almacena en el directorio \bin de Visual Basic y el directorio \bin\debug de C#).  
  
 Puede habilitar la protección en la copia del documento que se abre en el Diseñador de cerrar el proyecto en Visual Studio, abra la copia del documento que se encuentra en el directorio del proyecto y activar la protección.  
  
## <a name="enforcing-word-document-protection-on-build"></a>Aplicar protección de documentos de Word en la compilación  
 Visual Studio inicia la aplicación de protección de documentos de Word y plantillas durante el proceso de compilación, para que la protección está habilitada cuando el documento se abre para la depuración. El documento está protegido con una contraseña vacía.  
  
 La protección está habilitada durante la compilación así que si hay código en el documento <xref:Microsoft.Office.Tools.Word.Document.Startup> eventos que podrían provocar excepciones o cambiar el comportamiento de la aplicación, este código puede ser depurado correctamente. Si habilita la protección después de abre el documento, no se puede depurar código de inicialización o se no se probó.  
  
## <a name="setting-the-password"></a>Configuración de la contraseña  
 Visual Studio automáticamente habilita la protección, pero no proporciona ninguna contraseña de forma predeterminada. Si desea que la protección del documento que tiene una contraseña, debe agregarlo antes de implementar la solución. Agregar una contraseña le permite dejar que los usuarios autorizados quitar la protección del documento; sin una contraseña, no puede eliminarse fácilmente protección. Para obtener más información acerca de cómo establecer una contraseña, vea la Ayuda de la aplicación de Office específica.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: proteger documentos y partes de documentos mediante programación](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Information Rights Management y la información general de las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protección con contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Cómo: permitir que el código ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Diseño y creación de soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  