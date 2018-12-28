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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 49b2e66f35bf320d6eca04fd1b171a5e0c65132e
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804791"
---
# <a name="grant-trust-to-office-solutions"></a>Conceder confianza a las soluciones de Office
  Conceder confianza a los medios de las soluciones de Office modificar la directiva de seguridad de cada equipo de destino debe confiar en el ensamblado de la solución, el manifiesto de aplicación, el manifiesto de implementación y el documento. Por usted o el usuario final, se puede conceder confianza a la solución de Office.

 Puede conceder plena confianza a la solución de Office mediante la firma de los manifiestos de aplicación e implementación.

 Los usuarios finales pueden conceder confianza a la solución de Office mediante la realización de una decisión de confianza en el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aviso de confianza.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

##  <a name="Signing"></a> Confiar en la solución de firmar los manifiestos de aplicación e implementación
 Manifiestos de aplicación y la implementación para Office solutions deben firmarse con un certificado que identifica al publicador. Los certificados proporcionan una base para tomar decisiones de confianza.

 Se crea un certificado temporal y se confía en tiempo de compilación para que la solución se ejecute mientras se depura. Si publica una solución que está firmada con un certificado temporal, se pedirá al usuario final para tomar una decisión de confianza.

 Si la sesión de la solución con un certificado conocido y de confianza, la solución se instalarán automáticamente sin preguntar al usuario final para tomar una decisión de confianza. Para obtener más información sobre cómo obtener un certificado para firmar, consulte [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md). Una vez obtenido un certificado, el certificado debe ser confiable explícitamente al agregarlo a la lista de editores de confianza. Para obtener más información, vea [Cómo: Agregar un publicador de confianza en un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Si suscribe a un desarrollador de la solución con un certificado temporal, un administrador puede volver a iniciar sesión la personalización con un certificado conocido y de confianza mediante el uso de la herramienta de edición y generación de manifiesto (*mage.exe*), que es uno de los Herramientas de Microsoft .NET Framework. Para obtener más información sobre la firma de soluciones, vea [Cómo: Firmar soluciones de Office](../vsto/how-to-sign-office-solutions.md) y [Cómo: Firmar manifiestos de aplicación e implementación](../ide/how-to-sign-application-and-deployment-manifests.md).

##  <a name="TrustPrompt"></a>Confiar en la solución utilizando el símbolo del sistema de confianza de ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pide al usuario final para tomar la decisión de confianza si no hay ninguna directiva de toda la organización que confía en el certificado de la solución. Si el usuario final concede confianza a la solución, se crea una entrada de la lista de inclusión que contiene una dirección URL y una clave pública para almacenar esta decisión de confianza. Cuando una personalización de confianza se ejecuta más tarde, el usuario final no se solicita a intentarlo.

 Los administradores pueden deshabilitar la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] confía en símbolo del sistema o requieren que el símbolo del sistema se producen solo para las soluciones que estén firmadas con un certificado Authenticode. Para obtener más información acerca de cómo cambiar esta configuración para las zonas MyComputer, LocalIntranet, Internet, TrustedSites y UntrustedSites, vea [Cómo: Configurar el comportamiento del mensaje de confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Vea también

- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Conceder confianza a los documentos](../vsto/granting-trust-to-documents.md)
- [Solucionar problemas de seguridad de la solución de Office](../vsto/troubleshooting-office-solution-security.md)
- [Consideraciones de seguridad específicas para soluciones de Office](../vsto/specific-security-considerations-for-office-solutions.md)