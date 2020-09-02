---
title: Permitir que el código se ejecute detrás de docs con permisos restringidos
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 15cfb7ebf2f4f71e892820206f0dd1d006639992
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547516"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Cómo: permitir que el código se ejecute en documentos con permisos restringidos
  Puede usar la característica de información Rights Management (IRM) de Microsoft Office para restringir los permisos a un documento o libro. De forma predeterminada, no se permite la ejecución del código que se encuentra detrás de un documento Microsoft Office Word restringido o Microsoft Office libro de Excel. Puede cambiar el valor predeterminado para que las extensiones de código administrado puedan tener acceso al modelo de objetos y la solución funcione.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Debe ser el autor del documento o libro o tener acceso de control total para poder cambiar la configuración de permisos.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Para permitir que el código se ejecute detrás de documentos con permisos restringidos

1. Abra el documento o el libro en Word o Excel.

2. Haga clic en la pestaña **archivo** , seleccione **preparar**, elija **restringir permisos**y, a continuación, haga clic en **acceso restringido**.

   > [!NOTE]
   > Al usarse por primera vez, se le pedirá que instale el cliente de Windows Rights Management. Después de instalar el cliente de, es posible que tenga que repetir los pasos.

3. En el cuadro de diálogo **permiso** , seleccione **restringir el permiso a este documento**y, a continuación, haga clic en **más opciones**.

4. En **permisos adicionales para los usuarios**, seleccione **acceso a contenido mediante programación**.

   Word o Excel permitirán el acceso mediante programación al modelo de objetos.

## <a name="see-also"></a>Vea también
- [Información general sobre Information Rights Management y extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
