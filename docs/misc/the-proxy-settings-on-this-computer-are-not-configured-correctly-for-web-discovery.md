---
title: "La configuraci&#243;n del proxy de este equipo no es la correcta para el descubrimiento Web. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_MUSTSPECIFYPROXYSERVER"
  - "vs.WebDiscoveryProxyHelp"
ms.assetid: aea2cc20-9180-47cb-b1ed-78fa5f8a407f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# La configuraci&#243;n del proxy de este equipo no es la correcta para el descubrimiento Web.
Este error aparece en el cuadro de diálogo Agregar referencia web si está desarrollando en un equipo que se encuentra tras un firewall y no se especificó explícitamente un servidor proxy para las conexiones de Internet Explorer. Para poner los servicios exteriores al firewall a disposición del explorador web en el cuadro de diálogo Agregar referencia web, deberá especificar explícitamente la dirección y el puerto del servidor proxy de la red. .NET Framework omite la opción de detección automática del servidor proxy para las conexiones de Internet Explorer. Puede que sea necesario solicitar al administrador de red esta información del proxy.  
  
 Para obtener más información sobre "Automatic Discovery for Firewall and Web Proxy Clients" \("Detección automática de los clientes de proxy web y firewall"\) vea: [http:\/\/www.microsoft.com\/technet\/prodtechnol\/isa\/2004\/plan\/automaticdiscovery.mspx](http://www.microsoft.com/technet/prodtechnol/isa/2004/plan/automaticdiscovery.mspx).  
  
### Para especificar un servidor proxy de Internet Explorer  
  
1.  En el menú **Herramientas**, elija **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, elija **Entorno** y, luego, **Explorador web**.  
  
3.  Haga clic en **Opciones de Internet Explorer**.  
  
4.  En la pestaña **Conexiones**, haga clic en **Configuración de LAN**.  
  
5.  Anule la selección de **Detectar la configuración automáticamente**.  
  
6.  En el área **Servidor proxy**, seleccione **Usar un servidor proxy para la LAN \(esta configuración no se aplicará a conexiones de acceso telefónico ni VPN\).**.  
  
7.  Especifique el número de puerto y la dirección que coincida con la red.  
  
8.  Haga clic en **Aceptar**, después de nuevo en **Aceptar** y, por último, otra vez en **Aceptar**.  
  
9. En el menú **Archivo**, elija **Salir** y vuelva a abrir Visual Studio.  
  
## Vea también  
 [Agregar referencia Web \(Cuadro de diálogo\)](http://msdn.microsoft.com/es-es/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Cómo: Agregar y quitar referencias Web](http://msdn.microsoft.com/es-es/a7ddaa5d-4672-405b-91b3-39de65d7e3a2)   
 [Programming the Web with XML Web Services](http://msdn.microsoft.com/es-es/2d651a26-73df-4b39-85fa-7913a7d6bee4)