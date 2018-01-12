---
title: "Cómo: permitir que el código ejecute en documentos con permisos restringidos | Documentos de Microsoft"
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
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 09336e72cc9e1e1bc0a407314d4fa9fd6bc2a2c9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Cómo: Permitir que el código se ejecute en documentos con permisos restringidos
  Puede usar la característica Information Rights Management (IRM) de Microsoft Office para restringir los permisos a un documento o libro. De forma predeterminada, no se permite ejecutar el código detrás de un documento restringido de Microsoft Office Word o un libro de Microsoft Office Excel. Puede cambiar el valor predeterminado para que las extensiones de código administrado pueden tener acceso al modelo de objeto y la solución funcionará.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Debe ser el autor del documento o libro o tener acceso de Control total para poder cambiar la configuración de permisos.  
  
### <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Para permitir que el código para que se ejecute en documentos con permisos restringidos  
  
1.  Abra el documento o libro en Word o Excel.  
  
2.  Haga clic en el **archivo** ficha, seleccione **preparar**, seleccione **restringir permisos**y, a continuación, haga clic en **acceso restringido**.  
  
    > [!NOTE]  
    >  Use por primera vez, deberá instalar al cliente de Windows Rights Management. Después de instalar al cliente, tendrá que repetir los pasos.  
  
3.  En el **permiso** cuadro de diálogo, seleccione **restringir permisos a este documento**y, a continuación, haga clic en **más opciones**.  
  
4.  En **permisos adicionales para los usuarios**, seleccione **acceder a contenido mediante programación**.  
  
 Word o Excel permitirá el acceso mediante programación al modelo de objetos.  
  
## <a name="see-also"></a>Vea también  
 [Information Rights Management y la información general de las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Protección con contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Implementación de una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  