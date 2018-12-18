---
title: Conceder confianza a las soluciones de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfce58ca765e7e3710ecb55a1c84c09f0ee14f52
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447250"
---
# <a name="grant-trust-to-office-solutions"></a>Conceder confianza a las soluciones de Office
  Conceder confianza a los medios de soluciones de Office modificar la directiva de seguridad de cada equipo de destino debe confiar en el ensamblado de la solución, el manifiesto de aplicación, el manifiesto de implementación y el documento. Se concede confianza a la solución de Office por usted o el usuario final.  
  
 Puede conceder plena confianza a la solución de Office mediante la firma de los manifiestos de aplicación e implementación.  
  
 Los usuarios finales pueden conceder confianza a la solución de Office mediante la realización de una decisión de confianza en la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aviso de confianza.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Confiar en la solución mediante la firma de los manifiestos de aplicación e implementación  
 Manifiestos de todas las aplicaciones e implementación para Office soluciones deben estar firmadas con un certificado que identifique al publicador. Los certificados proporcionan una base para tomar decisiones de confianza.  
  
 Un certificado temporal se crea automáticamente y se concede confianza en tiempo de compilación, por lo que se ejecutará la solución mientras se depura. Si publica una solución que está firmada con un certificado temporal, se pedirá al usuario final para tomar una decisión de confianza.  
  
 Si se registra la solución con un certificado conocido y de confianza, la solución se instalará automáticamente sin preguntar al usuario final para tomar una decisión de confianza. Para obtener más información acerca de cómo obtener un certificado de firma, vea [ClickOnce y Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Una vez obtenido un certificado, el certificado debe ser de confianza explícitamente, éste se agrega a la lista de editores de confianza. Para obtener más información, consulte [Cómo: agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Si un programador firma la solución con un certificado temporal, un administrador puede volver a iniciar sesión la personalización con un certificado conocido y de confianza mediante el uso de la herramienta de edición y generación de manifiestos (*mage.exe*), que es uno de los Herramientas de Microsoft .NET Framework. Para obtener más información acerca de cómo firmar soluciones, consulte [Cómo: soluciones de Office de inicio de sesión](../vsto/how-to-sign-office-solutions.md) y [Cómo: firmar los manifiestos de aplicación e implementación](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Confiar en la solución utilizando el aviso de confianza de ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] solicita al usuario final para tomar la decisión de confianza si no hay ninguna directiva de toda la organización que confía en los certificados de la solución. Si el usuario final concede confianza a la solución, se crea una entrada de la lista de inclusión que contiene una dirección URL y una clave pública para almacenar esta decisión de confianza. Cuando una personalización de confianza se ejecuta más tarde, el usuario final no se pide de nuevo.  
  
 Los administradores pueden deshabilitar la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confía en símbolo del sistema o requieren que el símbolo del sistema se producen solo para las soluciones que estén firmadas con un certificado Authenticode. Para obtener más información acerca de cómo cambiar esta configuración para las zonas MyComputer, intranet local, Internet, TrustedSites y UntrustedSites, vea [Cómo: configurar el comportamiento de solicitud de confianza de ClickOnce](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Vea también  
 [Proteger soluciones de Office](../vsto/securing-office-solutions.md)   
 [Conceder confianza a documentos](../vsto/granting-trust-to-documents.md)   
 [Solucionar problemas de seguridad de la solución de Office](../vsto/troubleshooting-office-solution-security.md)   
 [Consideraciones de seguridad específicas para soluciones de Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  