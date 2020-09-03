---
title: Protección de documentos en soluciones de nivel de documento
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c5f019907495c3cad3fddef501455aedf345bb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "71253805"
---
# <a name="document-protection-in-document-level-solutions"></a>Protección de documentos en soluciones de nivel de documento
  Puede usar las características de protección de Microsoft Office Word y Microsoft Office Excel en los proyectos de nivel de documento. Estas características impiden que los usuarios no autorizados realicen cambios en las partes protegidas de un documento.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Con Excel, puede activar y desactivar la protección mientras el libro está abierto en el diseñador. Con Word, solo puede activar la protección fuera del diseñador. En tiempo de ejecución, puede habilitar o deshabilitar la protección mediante programación para Word y Excel.

 Cuando está habilitada la protección de documentos en un documento que está abierto en el diseñador, todos los controles se quitan del **cuadro de herramientas** o dejan de estar disponibles, y no se puede arrastrar nada desde la ventana **orígenes de datos** hasta el documento.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument y documentos protegidos
 Si un documento está protegido, no se puede tener acceso a la memoria caché de datos desde fuera del documento. No puede utilizar la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase para recuperar o manipular los datos almacenados en caché en un documento protegido, ni usar otros métodos de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase.

## <a name="word-document-protection-in-the-designer"></a>Protección de documentos de Word en el diseñador
 Si agrega protección a un documento o plantilla de Word mientras está abierto en Visual Studio, no puede empezar a aplicar la protección en el diseñador. El documento está en modo de diseño mientras está abierto en Visual Studio y debe estar en modo de ejecución antes de poder comenzar a aplicar la protección.

 Sin embargo, si crea un proyecto que usa un documento de Word existente que tiene habilitada la protección, el documento se protege mientras está abierto en el diseñador. No se pueden editar las partes protegidas del documento, pero todavía se puede escribir código en el editor de código para automatizar el documento. Tampoco puede compilar el proyecto si está habilitada la protección mientras el documento está abierto en Visual Studio.

 Puede desactivar la protección mientras el documento está abierto en el diseñador para que pueda editar el documento y compilar el proyecto. No se puede desactivar la protección de la copia en el diseñador durante la depuración; el documento que se abre durante la depuración es una copia independiente de la abierta en el diseñador (la copia de salida se almacena en el directorio *\Bin* de Visual Basic y el directorio *\bin\debug* para C#).

 Puede habilitar la protección en la copia del documento que se abre en el diseñador cerrando el proyecto en Visual Studio, abriendo la copia del documento que se encuentra en el directorio del proyecto y activando la protección.

## <a name="enforce-word-document-protection-on-build"></a>Forzar la protección de documentos de Word al compilar
 Visual Studio comienza a aplicar la protección de documentos y plantillas de Word durante el proceso de compilación, de modo que se habilita la protección cuando el documento se abre para la depuración. El documento está protegido con una contraseña vacía.

 La protección se habilita durante la compilación, de modo que si hay código en el evento del documento <xref:Microsoft.Office.Tools.Word.Document.Startup> que puede provocar excepciones o cambiar el comportamiento de la aplicación, este código se puede depurar correctamente. Si habilita la protección después de abrir el documento, no se puede depurar o probar el código de inicialización.

## <a name="setting-the-password"></a>Establecimiento de la contraseña
 Visual Studio habilita automáticamente la protección, pero no proporciona ninguna contraseña de forma predeterminada. Si desea que la protección del documento tenga una contraseña, debe agregarla antes de implementar la solución. Agregar una contraseña le permite permitir que los usuarios autorizados quiten la protección del documento. sin una contraseña, la protección no se puede quitar fácilmente. Para obtener más información acerca de cómo establecer una contraseña, vea la ayuda de en la aplicación de Office específica.

## <a name="see-also"></a>Consulte también
- [Cómo: proteger documentos y partes de documentos mediante programación](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Información general sobre Information Rights Management y extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)
- [Cómo: permitir que el código se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
