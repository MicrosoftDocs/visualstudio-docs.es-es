---
title: "Otorgar confianza a las soluciones de Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "seguridad [desarrollo de Office en Visual Studio], confianza"
  - "listas de inclusión [desarrollo de Office en Visual Studio], acerca de las listas de inclusión"
  - "confianza [desarrollo de Office en Visual Studio], sistema 2007 Office"
  - "otorgar confianza [desarrollo de Office en Visual Studio]"
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Otorgar confianza a las soluciones de Office
  Otorgar confianza a las soluciones de Office significa modificar la directiva de seguridad de cada equipo de destino para confiar en el ensamblado, el manifiesto de aplicación, el manifiesto de implementación, y el documento de la solución.  La se puede conceder confianza a la solución de Office por usted o el usuario final.  
  
 Puede conceder plena confianza a la solución de Office firmar los manifiestos de aplicación e implementación.  
  
 Los usuarios finales pueden conceder confianza a la solución de Office creando una decisión de confianza en el indicador confiable de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Confirmando la solución firmar la aplicación y los manifiestos de implementación  
 Todos los manifiestos de aplicación e implementación de soluciones de Office se deben firmar con un certificado que identifique al publicador.  Los certificados proporcionan una base para tomar decisiones de confianza.  
  
 En tiempo de compilación se crea automáticamente un certificado temporal al que se concede confianza para que la solución se ejecute mientras se depura.  Si publica una solución que esté firmado con un certificado temporal, se solicitará al usuario final para tomar una decisión de confianza.  
  
 Si firma la solución con un certificado conocido y de confianza, la solución se instalará automáticamente sin pedir al usuario final que tome una decisión de confianza.  Para obtener más información sobre cómo obtener un certificado para la firma, vea [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md).  Una vez obtenido un certificado, debe confiarse en él explícitamente agregándolo a la lista de editores de confianza.  Para obtener más información, vea [Cómo: Agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](~/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
 Si un programador firma la solución con un certificado temporal, el administrador puede volver a firmar la personalización con un certificado conocido y de confianza mediante la herramienta de generación y edición de manifiestos \(mage.exe\), una de las herramientas de Microsoft .NET Framework.  Para obtener más información sobre la firma de soluciones, vea [Cómo: Firmar soluciones de Office](../vsto/how-to-sign-office-solutions.md) y [Cómo: Firmar aplicaciones y manifiestos de implementación](~/ide/how-to-sign-application-and-deployment-manifests.md).  
  
##  <a name="TrustPrompt"></a> Confiar en la solución utilizando el mensaje de ClickOnce relativo a la confianza  
 Si no existe una directiva de la organización que confíe en el certificado de la solución, [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pide confirmación al usuario final para tomar la decisión de confianza.  Si el usuario final concede confianza a la solución, se crea una entrada en la lista de inclusión que contiene una dirección URL y una clave pública para almacenar esta decisión de confianza.  Cuando se ejecuta una personalización de confianza más adelante, no se pide confirmación de nuevo al usuario final.  
  
 Los administradores pueden deshabilitar el mensaje relativo a la confianza de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] o bien pueden requerir que el mensaje sólo se produzca en soluciones firmadas con un certificado Authenticode.  Para obtener más información sobre cómo cambiar esta configuración en las zonas MyComputer, LocalIntranet, Internet, TrustedSites y UntrustedSites, vea [Cómo: Configurar el comportamiento del mensaje relativo a la confianza de ClickOnce](~/deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Otorgar confianza a los documentos](../vsto/granting-trust-to-documents.md)   
 [Solucionar problemas de seguridad de soluciones de Office](../vsto/troubleshooting-office-solution-security.md)   
 [Consideraciones de seguridad específicas para soluciones de Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  