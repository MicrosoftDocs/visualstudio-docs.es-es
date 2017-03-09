---
title: "Soluci&#243;n de problemas de excepciones: System.ServiceModel.Security.MessageSecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.ServiceModel.Security.MessageSecurityException (excepción)"
  - "MessageSecurityException (excepción)"
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.ServiceModel.Security.MessageSecurityException
Se produce una excepción <xref:System.ServiceModel.Security.MessageSecurityException> cuando [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] determina que un mensaje no se ha protegido correctamente o se ha manipulado. El error se produce con más frecuencia cuando se cumplen todas las condiciones siguientes:  
  
-   Se usa una referencia de servicio WCF sobre una conexión remota, como Conexión a Escritorio remoto o Terminal Services, para comunicarse con un servicio WCF \(.svc\) en un sitio web o proyecto de aplicación web.  
  
-   No tiene permisos de administrador en el sitio remoto.  
  
-   El servidor de desarrollo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] controla las solicitudes al host local en el sitio remoto.  
  
## Sugerencias asociadas  
 **Resuelva los problemas de autenticación de NTLM cuando use el servidor de desarrollo de ASP.Net.**  
 El servidor de desarrollo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] suele tener desactivada la seguridad de Desafío\/Respuesta de Windows NT \(NTLM\), lo que permite el acceso anónimo. De forma predeterminada, al ejecutar una sesión de Terminal Services o utilizar una conexión remota, la seguridad NTLM está habilitada. Cuando NTLM está habilitada, todas las solicitudes al host local se validan con las credenciales del usuario o proceso que inició el servidor de desarrollo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Esto reduce las amenazas de seguridad. Sin embargo, WCF también realiza su propia autenticación y no permite que una cuenta que no sea de administrador utilice servicios WCF.  
  
 Si un usuario remoto ejecutara el sitio web mediante el servidor de desarrollo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y, además, trabajara con un servicio Web o un servicio WCF, puede crear un enlace de servicio personalizado o bien desactivar la seguridad NTLM.  
  
> [!IMPORTANT]
>  No se recomienda desactivar la seguridad NTLM; además constituye una amenaza de seguridad.  
  
 Si crea un servicio personalizado de enlace, la autenticación NTLM continúa proporcionando protección.  
  
 Realice los pasos siguientes para crear un servicio personalizado de enlace para el servicio WCF.  
  
#### Para crear un servicio personalizado de enlace para el servicio WCF hospedado dentro del servidor de desarrollo de ASP.NET  
  
1.  Abra el archivo Web.config para el servicio WCF que está generando la excepción.  
  
2.  Escriba la información siguiente en el archivo Web.config.  
  
    ```  
    <bindings> <customBinding> <binding name="Service1Binding"> <transactionFlow /> <textMessageEncoding /> <httpTransport authenticationScheme="Ntlm" /> </binding> </customBinding> </bindings>  
    ```  
  
3.  Guarde y cierre el archivo Web.config.  
  
4.  En el código del servicio WCF o servicio Web, cambie el valor de extremo como aparece a continuación:  
  
    ```  
    <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
    ```  
  
     Esto garantiza que el servicio utilice el enlace personalizado.  
  
5.  Agregue una referencia al servicio en la aplicación web que tiene acceso al servicio. \(En el cuadro de diálogo **Agregar referencia de servicio**, agregue una referencia al servicio como en el servicio original que generaba la excepción.\)  
  
 Puede realizar estos pasos para deshabilitar la seguridad NTLM cuando trabaje con una referencia del servicio WCF.  
  
> [!IMPORTANT]
>  No se recomienda desactivar la seguridad NTLM; además constituye una amenaza de seguridad.  
  
#### Desactivar la seguridad NTLM  
  
1.  En el **Explorador de soluciones**, haga clic en con el botón secundario en el nombre del sitio web y, a continuación, haga clic en **Páginas de propiedades**.  
  
2.  Seleccione **Opciones de inicio** y, a continuación, desactive la casilla **Autenticación NTLM**.  
  
3.  Haga clic en **Aceptar**.  
  
## Vea también  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)