---
title: "Implementaci&#243;n segura"
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
  - "implementación ClickOnce [desarrollo de Office en Visual Studio], seguridad"
  - "implementar aplicaciones [desarrollo de Office en Visual Studio], seguridad"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], seguridad"
  - "desarrollo de Office en Visual Studio, seguridad"
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Implementaci&#243;n segura
  Cuando se crea una solución de Office, el equipo de desarrollo se actualiza automáticamente para permitir que se ejecute el código en el proyecto.  Sin embargo, al implementar la solución, debe proporcionar pruebas en las que basar una decisión de confianza firmando la solución con un certificado o utilizando la clave de mensajes relativos a la confianza de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  Para obtener más información, vea [Otorgar confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 En las personalizaciones de nivel de documento, si implementa el documento en una ubicación de red, también debe agregar la ubicación del documento a la lista de ubicaciones de confianza del Centro de confianza de la aplicación de Office.  Para obtener más información sobre cómo establecer permisos de documentos en equipos de usuarios finales, vea [Otorgar confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
## Evitar que las soluciones de Office ejecuten código  
 Los administradores pueden utilizar el Registro para evitar que todas las soluciones de Office se ejecuten en un equipo.  Cuando se abre una solución de Office que tiene extensiones de código administrado, el motor en tiempo de ejecución de Visual Studio Tools para Office comprueba si una entrada con el nombre `Disabled` existe en una de las siguientes claves del Registro en el equipo:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Para evitar que las soluciones de Office ejecuten código, cree una entrada `Disabled` en una de estas claves del Registro, o en ambas, y especifique uno de los siguientes tipos de datos y valores para `Disabled`:  
  
-   REG\_SZ o REG\_EXPAND\_SZ que se establece en cualquier cadena distinta de "0" \(cero\).  
  
-   REG\_DWORD que se establece en cualquier valor distinto de 0 \(cero\).  
  
 Para permitir que las soluciones de Office ejecuten código, establezca las dos entradas de `Disabled` en 0 \(cero\) o elimine las entradas del Registro.  
  
## Vea también  
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Preparar equipos para ejecutar u hospedar soluciones de Office](http://msdn.microsoft.com/es-es/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)  
  
  