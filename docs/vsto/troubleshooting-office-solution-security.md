---
title: "Solucionar problemas de seguridad de soluciones de Office | Microsoft Docs"
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
  - "seguridad [desarrollo de Office en Visual Studio], solucionar problemas"
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Solucionar problemas de seguridad de soluciones de Office
  Este tema contiene sugerencias para solucionar problemas comunes que podrían producirse al trabajar en la seguridad de las soluciones de Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## No se pueden instalar soluciones de confianza desde sitios restringidos  
 Los usuarios no pueden instalar una solución desde una ubicación web si el sitio Web se encuentra en la zona de sitios restringidos de Internet Explorer.  Esto es así incluso cuando la solución está firmada con un certificado de confianza.  
  
 La dirección URL del manifiesto de implementación se puede dividir por categorías en cinco zonas:  
  
-   Mi PC  
  
-   Internet  
  
-   Intranet local  
  
-   Sitios de confianza  
  
-   Sitios restringidos  
  
 Si la ubicación del manifiesto de implementación se ha asignado a la zona de sitios restringidos, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] no instala la solución.  Si el usuario conoce la ubicación y considera que es de confianza, puede quitarla de la zona de sitios restringidos e instalar la solución.  Para obtener información sobre cómo administrar zonas, vea [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## No se pueden instalar soluciones desde recursos compartido de archivos de red o desde ubicaciones web cuando se ha instalado Configuración de seguridad mejorada de Internet Explorer o Internet Explorer 7  
 Configuración de seguridad mejorada de Internet Explorer \(IEESC\) en Windows Server 2003 y posterior, e Internet Explorer 7 y posterior, limita significativamente la capacidad de usuarios de examinar internet.  Cuando los usuarios intentan instalar soluciones de Office desde un recurso compartido de archivos de red o una ubicación del web, puede recibir el siguiente mensaje de error: “La funcionalidad personalizada en esta aplicación no funcionará porque el certificado utilizado para firmar el manifiesto de implementación para *SolutionName* no es de confianza.  Póngase en contacto con el administrador para obtener asistencia."  
  
 Con IEESC e Internet Explorer 7 y posterior, si clasifican la dirección URL del manifiesto de implementación en la zona de Internet, el manifiesto tiene un certificado de un editor de confianza o la solución no se puede instalar.  Sin IEESC, el comportamiento predeterminado es pedir confirmación al usuario final para tomar una decisión de confianza.  
  
 Para administrar el efecto de IEESC e Internet Explorer 7 y posterior, identifique los sitios Web y las rutas universales de \(UNC\) de convención de nomenclatura que confía y agrega a una de las zonas de seguridad \(intranet local o sitios de confianza\). Para obtener información sobre cómo administrar zonas, vea [Editores de confianza de configuración de ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)  
  
  