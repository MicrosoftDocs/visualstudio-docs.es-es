---
title: Conceder confianza a las soluciones de Office
description: Para conceder confianza a las soluciones de Office, debe modificar la Directiva de seguridad de cada equipo de destino para que confíe en el ensamblado de la solución, el manifiesto de implementación y el documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f98f3154a0708ce7a01603968f0f5774dd86f40e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910232"
---
# <a name="grant-trust-to-office-solutions"></a>Conceder confianza a las soluciones de Office
  Conceder confianza a las soluciones de Office significa modificar la Directiva de seguridad de cada equipo de destino para que confíe en el ensamblado de la solución, el manifiesto de la aplicación, el manifiesto de implementación y el documento. Tanto usted como el usuario final pueden conceder confianza a la solución de Office.

 Puede conceder plena confianza a la solución de Office mediante la firma de los manifiestos de aplicación y de implementación.

 Los usuarios finales pueden conceder confianza a la solución de Office al tomar una decisión de confianza en el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aviso de confianza.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Confiar en la solución mediante la firma de los manifiestos de aplicación e implementación
 Todos los manifiestos de aplicación e implementación de las soluciones de Office deben estar firmados con un certificado que identifique al publicador. Los certificados proporcionan una base para tomar decisiones de confianza.

 Se crea un certificado temporal y se le concede confianza en tiempo de compilación para que la solución se ejecute mientras se depura. Si publica una solución que está firmada con un certificado temporal, se le pedirá al usuario final que tome una decisión de confianza.

 Si firma la solución con un certificado conocido y de confianza, la solución se instalará automáticamente sin preguntar al usuario final que tome una decisión de confianza. Para obtener más información sobre cómo obtener un certificado para firmar, vea [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md). Después de obtener un certificado, el certificado debe ser de confianza explícita; para ello, agréguelo a la lista de editores de confianza. Para obtener más información, consulte [Cómo: agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Si un desarrollador firma la solución con un certificado temporal, un administrador puede volver a firmar la personalización con un certificado conocido y de confianza mediante el Herramienta de generación y edición de manifiestos (*mage.exe*), que es una de las herramientas de Microsoft .NET Framework. Para obtener más información acerca de la firma de soluciones, consulte [Cómo: firmar soluciones de Office](../vsto/how-to-sign-office-solutions.md) y [Cómo: firmar manifiestos de aplicación y de implementación](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Confiar en la solución mediante el mensaje de confianza de ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] solicita al usuario final que tome la decisión de confianza si no hay ninguna directiva de toda la organización que confíe en el certificado de la solución. Si el usuario final concede confianza a la solución, se crea una entrada de la lista de inclusión que contiene una dirección URL y una clave pública para almacenar esta decisión de confianza. Cuando una personalización de confianza se ejecuta más tarde, no se vuelve a preguntar al usuario final.

 Los administradores pueden deshabilitar el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] mensaje de confianza o requerir que el mensaje se produzca solo para las soluciones que estén firmadas con un certificado Authenticode. Para obtener más información sobre cómo cambiar esta configuración para las zonas de equipo, LocalIntranet, Internet, TrustedSites y UntrustedSites, consulte [Cómo: configurar el comportamiento del mensaje de confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Vea también

- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Conceder confianza a los documentos](../vsto/granting-trust-to-documents.md)
- [Solucionar problemas de seguridad de soluciones de Office](../vsto/troubleshooting-office-solution-security.md)
- [Consideraciones de seguridad específicas para las soluciones de Office](../vsto/specific-security-considerations-for-office-solutions.md)