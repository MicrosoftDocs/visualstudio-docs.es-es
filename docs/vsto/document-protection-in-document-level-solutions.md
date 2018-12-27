---
title: Protección de documentos en soluciones de nivel de documento
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 03724e523c1f49277e0bc2b23465d5296d806695
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648540"
---
# <a name="document-protection-in-document-level-solutions"></a>Protección de documentos en soluciones de nivel de documento
  Puede usar las características de protección de Microsoft Office Word y Microsoft Office Excel en los proyectos de nivel de documento. Estas características impiden que los usuarios no autorizados puedan realizar cambios en elementos protegidos de un documento.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Con Excel, puede activar y desactivar la protección mientras el libro está abierto en el diseñador. Con Word, puede activar la protección sólo fuera del diseñador. En tiempo de ejecución, puede habilitar o deshabilitar la protección mediante programación de Word y Excel.  
  
 Cuando se habilita la protección de documentos en un documento que está abierto en el diseñador, se quitan todos los controles de la **cuadro de herramientas** o dejan de estar disponibles, y no puede arrastrar cualquier cosa, desde el **orígenes de datos** ventana de documento.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument y documentos protegidos  
 Si un documento está protegido, la caché de datos no es accesible desde fuera del documento. No puede usar el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase para recuperar o manipular los datos que se almacena en caché en un documento protegido, o utilizar otros métodos de la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> clase.  
  
## <a name="word-document-protection-in-the-designer"></a>Protección de documentos de Word en el diseñador  
 Si agrega protección a un documento de Word o una plantilla mientras está abierto en Visual Studio, no puede empezar a aplicar la protección en el diseñador. El documento está en modo de diseño mientras está abierto en Visual Studio y debe estar en modo de ejecución antes de empezar a aplicar la protección.  
  
 Sin embargo, si crea un proyecto que usa un documento de Word existente que tiene habilitada la protección, el documento está protegido mientras está abierto en el diseñador. No se puede editar las partes del documento protegidas, pero todavía puede escribir código en el Editor de código para automatizar el documento. También, no se puede compilar el proyecto si está habilitada la protección mientras el documento está abierto en Visual Studio.  
  
 Puede desactivar protección mientras el documento está abierto en el diseñador para que pueda editar el documento y compile el proyecto. No se puede desactivar la protección para la copia en el diseñador durante la depuración; el documento que se abre durante la depuración es una copia independiente de la que está abierta en el diseñador (la salida se almacena en el *\bin* directorio Visual Basic y el *\bin\debug* directorio para C#).  
  
 Puede habilitar la protección en la copia del documento que se abre en el diseñador, cuando se cierra el proyecto en Visual Studio, abra la copia del documento que se encuentra en el directorio del proyecto y activar la protección.  
  
## <a name="enforce-word-document-protection-on-build"></a>Aplicar la protección de documento de Word en la compilación  
 Visual Studio comienza a aplicar la protección de documentos de Word y plantillas durante el proceso de compilación para que la protección está habilitada cuando se abre el documento para la depuración. El documento está protegido con una contraseña vacía.  
  
 Protección está habilitada durante la compilación así que si hay código en el documento <xref:Microsoft.Office.Tools.Word.Document.Startup> eventos que pueden producir excepciones o cambiar el comportamiento de la aplicación, este código puede ser depurado correctamente. Si habilita la protección después de abre el documento, el código de inicialización no puede depurar ni se probado.  
  
## <a name="setting-the-password"></a>Configuración de la contraseña  
 Visual Studio habilita la protección automáticamente, pero no proporciona ninguna contraseña de forma predeterminada. Si desea que la protección de documentos para tener una contraseña, debe agregarlo antes de implementar la solución. Agregar una contraseña le permite dejar que los usuarios autorizados quitar la protección del documento; sin una contraseña, no puede quitarse fácilmente protección. Para obtener más información acerca de cómo establecer una contraseña, vea la Ayuda de la aplicación de Office específica.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Proteger documentos y partes de documentos mediante programación](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Information rights management y la introducción a las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Cómo: Permitir que el código se ejecute detrás de documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  