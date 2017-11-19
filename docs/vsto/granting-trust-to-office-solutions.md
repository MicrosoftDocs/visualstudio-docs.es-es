---
title: Otorgar confianza a las soluciones de Office | Documentos de Microsoft
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
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: da7f4695bc817a66761c579b4c5af85b59ee041f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="granting-trust-to-office-solutions"></a>Otorgar confianza a las soluciones de Office
  Otorgar confianza a las soluciones de Office significa modificar la directiva de seguridad de cada equipo de destino debe confiar en el ensamblado de la solución, el manifiesto de aplicación, el manifiesto de implementación y el documento. Se concede confianza a la solución de Office por usted o el usuario final.  
  
 Puede conceder plena confianza a la solución de Office mediante la firma de los manifiestos de aplicación e implementación.  
  
 Los usuarios finales pueden conceder confianza a la solución de Office mediante la realización de una decisión de confianza en la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aviso de confianza.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a>Manifiestos de confiar en la solución mediante la firma de la aplicación e implementación  
 Manifiestos de todas las aplicaciones e implementación para Office soluciones deben estar firmadas con un certificado que identifique al publicador. Los certificados proporcionan una base para tomar decisiones de confianza.  
  
 Un certificado temporal se crea automáticamente y se concede confianza en tiempo de compilación, por lo que se ejecutará la solución mientras se depura. Si publica una solución que está firmada con un certificado temporal, se pedirá al usuario final para tomar una decisión de confianza.  
  
 Si se registra la solución con un certificado conocido y de confianza, la solución se instalará automáticamente sin preguntar al usuario final para tomar una decisión de confianza. Para obtener más información acerca de cómo obtener un certificado de firma, vea [ClickOnce y Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Una vez obtenido un certificado, el certificado debe ser de confianza explícitamente, éste se agrega a la lista de editores de confianza. Para obtener más información, consulte [Cómo: agregar un publicador de confianza en un equipo cliente para aplicaciones ClickOnce](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Si un programador firma la solución con un certificado temporal, un administrador puede volver a firmar la personalización con un certificado conocido y de confianza mediante la generación de manifiestos y la herramienta de edición (mage.exe), que es una de las herramientas de Microsoft .NET Framework. Para obtener más información acerca de cómo firmar soluciones, consulte [Cómo: soluciones de Office de inicio de sesión](../vsto/how-to-sign-office-solutions.md) y [Cómo: firmar aplicaciones y manifiestos de implementación](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Otorgar confianza a la solución mediante el símbolo del sistema de la confianza de ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]solicita al usuario final para tomar la decisión de confianza si no hay ninguna directiva de toda la organización que confía en los certificados de la solución. Si el usuario final concede confianza a la solución, se crea una entrada de la lista de inclusión que contiene una dirección URL y una clave pública para almacenar esta decisión de confianza. Cuando una personalización de confianza se ejecuta más tarde, el usuario final no se pide de nuevo.  
  
 Los administradores pueden deshabilitar la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confía en símbolo del sistema o requieren que el símbolo del sistema se producen solo para las soluciones que estén firmadas con un certificado Authenticode. Para obtener más información acerca de cómo cambiar esta configuración para las zonas MyComputer, intranet local, Internet, TrustedSites y UntrustedSites, vea [Cómo: configurar el comportamiento de solicitud de confianza de ClickOnce](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Otorgar confianza a los documentos](../vsto/granting-trust-to-documents.md)   
 [Solucionar problemas de seguridad de la solución de Office](../vsto/troubleshooting-office-solution-security.md)   
 [Consideraciones de seguridad específicas para soluciones de Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  