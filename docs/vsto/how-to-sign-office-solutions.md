---
title: "Cómo: firmar soluciones de Office | Documentos de Microsoft"
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
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 12a367b6051f7ed1ca1f51e0c9d7e8ada4be4ba6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-sign-office-solutions"></a>Cómo: Firmar soluciones de Office
  Si se registra una solución, puede conceder confianza a la solución utilizando el certificado como prueba. Puede utilizar el mismo certificado para varias soluciones y todas las soluciones serán de confianza sin actualizaciones de directiva de seguridad adicional.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si modifica manualmente la aplicación y los manifiestos de implementación mediante la generación de manifiestos y la herramienta de edición (mage.exe y mageui.exe), debe volver a firmar los manifiestos antes de utilizarlas. Para obtener más información, consulta [How to: Re-sign Application and Deployment Manifests](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="signing-by-using-a-certificate"></a>Mediante un certificado de firma  
 Un certificado es un archivo que contiene una clave única y la identidad del Editor de la solución. Puede adquirir certificados de una entidad de certificación, o crear su propio certificado y tiene una entidad de certificación a firmar.  
  
 Visual Studio firma soluciones de Office con un certificado temporal para habilitar la depuración. No se debe usar el certificado temporal en las soluciones implementadas como prueba.  
  
#### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Para firmar una solución de Office mediante un certificado  
  
1.  En el **proyecto** menú, haga clic en *nombresolución***propiedades**.  
  
2.  Haga clic en la pestaña **Firma**.  
  
3.  Seleccione **firmar los manifiestos de ClickOnce**.  
  
4.  Busque el certificado haciendo clic en **seleccionar del almacén** o **seleccionar del archivo** y navegar hasta el certificado.  
  
5.  Para comprobar que se está usando el certificado correcto, haga clic en **más detalles** para ver la información del certificado.  
  
## <a name="see-also"></a>Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Otorgar confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)   
 [Página Firma, Diseñador de proyectos](/visualstudio/ide/reference/signing-page-project-designer)  
  
  