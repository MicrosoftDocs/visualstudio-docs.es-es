---
title: 'Cómo: firmar soluciones de Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 161c175b6bb37ece93559f0378bbaf8e5e16d170
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776138"
---
# <a name="how-to-sign-office-solutions"></a>Cómo: firmar soluciones de Office
  Si inicia sesión una solución, puede conceder confianza a la solución utilizando el certificado como prueba. Puede usar el mismo certificado para varias soluciones y todas las soluciones serán de confianza sin actualizaciones de directiva de seguridad adicional.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si edita manualmente la aplicación y los manifiestos de implementación mediante el uso de la herramienta de edición y generación de manifiesto (*mage.exe* y *mageui.exe*), deberá volver a firmar los manifiestos antes de usarlos. Para obtener más información, consulte [Cómo: volver a firmar manifiestos de aplicación e implementación](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="sign-by-using-a-certificate"></a>Inicie sesión con un certificado  
 Un certificado es un archivo que contiene una clave única y la identidad del Editor de la solución. Puede adquirir certificados de una entidad de certificación, o crear su propio certificado y tiene una entidad de certificación de firmarlo.  
  
 Visual Studio firma soluciones de Office con un certificado temporal para habilitar la depuración. No se debe usar el certificado temporal en soluciones implementadas como evidencia.  
  
### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Para iniciar sesión con un certificado de una solución de Office  
  
1.  En el **proyecto** menú, haga clic en _SolutionName_**propiedades**.  
  
2.  Haga clic en la pestaña **Firma**.  
  
3.  Seleccione **firmar los manifiestos de ClickOnce**.  
  
4.  Busque el certificado, haga clic en **seleccione de Store** o **seleccionar del archivo** y navegar hasta el certificado.  
  
5.  Para comprobar que se está utilizando el certificado correcto, haga clic en **más detalles** para ver la información del certificado.  
  
## <a name="see-also"></a>Vea también  
 [Proteger soluciones de Office](../vsto/securing-office-solutions.md)   
 [Conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)   
 [Página Firma, Diseñador de proyectos](/visualstudio/ide/reference/signing-page-project-designer)  
  
  