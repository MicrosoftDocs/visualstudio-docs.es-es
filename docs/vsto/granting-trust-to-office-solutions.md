---
title: Conceder confianza a las soluciones de Office
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301660"
---
# <a name="grant-trust-to-office-solutions"></a>Conceder confianza a las soluciones de Office
  Conceder confianza a las soluciones de Office significa modificar la directiva de seguridad de cada equipo de destino para confiar en el ensamblado de la solución, el manifiesto de aplicación, el manifiesto de implementación y el documento. Usted o el usuario final pueden conceder confianza a la solución de Office.

 Puede conceder plena confianza a la solución de Office firmando los manifiestos de aplicación e implementación.

 Los usuarios finales pueden conceder confianza a [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] la solución de Office tomando una decisión de confianza en el símbolo del sistema de confianza.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>Confíe en la solución firmando los manifiestos de aplicación e implementación
 Todos los manifiestos de aplicación e implementación para las soluciones de Office deben firmarse con un certificado que identifique al publicador. Los certificados proporcionan una base para tomar decisiones de confianza.

 Se crea un certificado temporal y se concede confianza en tiempo de compilación para que la solución se ejecute mientras se depura. Si publica una solución firmada con un certificado temporal, se pedirá al usuario final que tome una decisión de confianza.

 Si firma la solución con un certificado conocido y de confianza, la solución se instalará automáticamente sin solicitar al usuario final que tome una decisión de confianza. Para obtener más información acerca de cómo obtener un certificado para la firma, vea [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md). Después de obtener un certificado, el certificado debe ser de confianza explícitamente agregándolo a la lista de editores de confianza. Para obtener más información, vea [Cómo: Agregar un publicador](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)de confianza a un equipo cliente para aplicaciones ClickOnce .

 Si un desarrollador firma la solución con un certificado temporal, un administrador puede volver a firmar la personalización con un certificado conocido y de confianza mediante la herramienta de generación y edición de manifiestos *(mage.exe*), que es una de las herramientas de Microsoft .NET Framework. Para obtener más información acerca de la firma de soluciones, vea [Cómo: firmar soluciones](../vsto/how-to-sign-office-solutions.md) de Office y [Cómo: firmar manifiestos de aplicación e implementación.](../ide/how-to-sign-application-and-deployment-manifests.md)

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Confíe en la solución mediante el símbolo del sistema clickOnce trust
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]solicita al usuario final que tome la decisión de confianza si no hay ninguna directiva de toda la organización que confíe en el certificado de la solución. Si el usuario final concede confianza a la solución, se crea una entrada de lista de inclusión que contiene una dirección URL y una clave pública para almacenar esta decisión de confianza. Cuando se ejecuta una personalización de confianza más adelante, no se vuelve a solicitar al usuario final.

 Los administradores [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pueden deshabilitar el mensaje de confianza o requerir que el mensaje se produzca solo para las soluciones que están firmadas con un certificado Authenticode. Para obtener más información acerca de cómo cambiar esta configuración para las zonas MyComputer, LocalIntranet, Internet, TrustedSites y UntrustedSites, vea [Cómo: configurar el comportamiento](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)de solicitud de confianza ClickOnce .

## <a name="see-also"></a>Consulte también

- [Soluciones de Secure Office](../vsto/securing-office-solutions.md)
- [Conceder confianza a los documentos](../vsto/granting-trust-to-documents.md)
- [Solucionar problemas de seguridad de la solución de Office](../vsto/troubleshooting-office-solution-security.md)
- [Consideraciones de seguridad específicas para las soluciones de Office](../vsto/specific-security-considerations-for-office-solutions.md)