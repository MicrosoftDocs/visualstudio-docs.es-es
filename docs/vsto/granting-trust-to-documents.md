---
title: "Otorgar confianza a los documentos | Microsoft Docs"
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
  - "otorgar confianza [desarrollo de Office en Visual Studio]"
  - "listas de inclusión [desarrollo de Office en Visual Studio], acerca de las listas de inclusión"
  - "seguridad [desarrollo de Office en Visual Studio], confianza"
  - "confianza [desarrollo de Office en Visual Studio], 2007 Office system"
ms.assetid: 16893647-501e-4836-98af-a79a1e9de3ee
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Otorgar confianza a los documentos
  Un proyecto de nivel de documento tiene los mismos requisitos de seguridad que los proyectos de nivel de aplicación, esto es, firmar los manifiestos con un certificado o hacer clic en el aviso de confianza.  Además, el documento o libro debe encontrarse en un directorio designado como ubicación de confianza.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Ubicaciones de confianza  
 Las aplicaciones de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y Office 2010 disponen de Centros de confianza en los que los usuarios pueden definir la configuración de seguridad y privacidad, como, por ejemplo, las ubicaciones de confianza.  En el caso de las soluciones de Office, el equipo local se considera una ubicación de confianza. Sin embargo, hay ciertos directorios que representan un riesgo más alto y que, por tanto, nunca pueden ser de confianza, como son las carpetas temporales del sistema, de cada usuario y de Internet Explorer.  
  
 Para obtener más información sobre el Trust Center, consulte [Seguridad, directivas y ajustes en Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202).  Para obtener más información acerca de cómo crear, administrar, eliminar y configurar carpetas de confianza, consulte [Configurar ubicaciones de confianza y editores de confianza en Office 2007 system](http://go.microsoft.com/fwlink/?LinkId=89203) y [Crear, eliminar o cambiar una ubicación de confianza para los archivos](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## Consideraciones de seguridad para soluciones de Office  
 Hay varias cuestiones de seguridad que se deben tener en cuenta al considerar las carpetas que desea agregar a las ubicaciones de confianza:  
  
-   Las carpetas locales se consideran más seguras y son de confianza de forma implícita.  Las ubicaciones remotas, como recursos compartidos de archivos, deben designarse como ubicaciones de confianza.  
  
-   Al agregar un directorio a las ubicaciones de confianza, se concede plena confianza no sólo a las soluciones de Office, sino también al código de VBA y ActiveX.  Por este motivo, el directorio raíz y las carpetas de Mis documentos no deben designarse como de confianza.  
  
-   Aunque al utilizar las ubicaciones de confianza, el propio documento es de confianza, se necesitan permisos adicionales para confiar en la personalización.  Puede conceder plena confianza a la personalización mediante la firma de manifiestos con un certificado, haciendo clic en el aviso de confianza o instalando la solución de Office en el directorio Archivos de programa.  
  
-   Puede almacenar el documento o libro de una solución de nivel de documento en el mismo directorio que el ensamblado o en otro directorio.  Por ejemplo, el documento podría estar ubicado en un servidor de SharePoint y el ensamblado en un recurso compartido de red.  Para obtener más información, consulte [Cómo: Publicar una solución de Office de nivel de documento en un servidor de SharePoint usando ClickOnce](http://msdn.microsoft.com/es-es/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## Vea también  
 [Otorgar confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)   
 [Solucionar problemas de seguridad de soluciones de Office](../vsto/troubleshooting-office-solution-security.md)   
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)  
  
  