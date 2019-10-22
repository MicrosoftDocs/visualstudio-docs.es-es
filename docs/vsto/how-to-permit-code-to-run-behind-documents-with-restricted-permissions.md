---
title: Permitir que el código se ejecute detrás de docs con permisos restringidos
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 32e42954958fda71d54c3c0ac2685928644e7461
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402246"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Procedimiento Permitir que el código se ejecute detrás de documentos con permisos restringidos
  Puede usar la característica Information Rights Management (IRM) de Microsoft Office para restringir permisos a un documento o libro. De forma predeterminada, el código detrás de un documento restringido de Microsoft Office Word o un libro de Microsoft Office Excel no se permite ejecutar. Puede cambiar el valor predeterminado para que sus extensiones de código administrado pueden obtener acceso al modelo de objeto y la solución funcionará.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Debe ser el autor del documento o libro o tener acceso de Control total para poder cambiar la configuración de permisos.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Para permitir que el código se ejecute detrás de documentos con permisos restringidos

1. Abra el documento o libro en Word o Excel.

2. Haga clic en el **archivo** pestaña, seleccione **preparar**, apunte a **restringir permisos**y, a continuación, haga clic en **acceso restringido**.

   > [!NOTE]
   > En el primer uso, deberá instalar al cliente de Windows Rights Management. Después de instalar al cliente, es posible que deba repetir los pasos.

3. En el **permiso** cuadro de diálogo, seleccione **restringir permisos a este documento**y, a continuación, haga clic en **más opciones**.

4. En **permisos adicionales para los usuarios**, seleccione **acceso a contenido mediante programación**.

   Word o Excel permitirá el acceso mediante programación al modelo de objetos.

## <a name="see-also"></a>Vea también
- [Information rights management y la introducción a las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
