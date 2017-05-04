---
title: "Otorgar confianza a las soluciones de Office mediante listas de inclusi&#243;n | Microsoft Docs"
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
  - "permisos [desarrollo de Office en Visual Studio]"
  - "listas de inclusión [desarrollo de Office en Visual Studio], acerca de las listas de inclusión"
  - "seguridad [desarrollo de Office en Visual Studio], listas de inclusión"
  - "listas de inclusión [desarrollo de Office en Visual Studio]"
ms.assetid: 6dae0128-435b-4fa1-aed9-73e728fdcacf
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Otorgar confianza a las soluciones de Office mediante listas de inclusi&#243;n
  Las listas de inclusión permiten a los usuarios decidir si las soluciones de Office firmadas con un certificado que identifique al publicador son fiables. Las listas de inclusión son específicas del usuario y se pueden usar en las personalizaciones de nivel de documento y en los complementos VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Cuando un usuario inicia una solución de Office que no se haya indicado como fiable, la solución de Microsoft Office le solicita que confirme si confía en esa solución mediante una pregunta de seguridad de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Si el usuario decide que la solución es fiable, la personalización se ejecuta y no se vuelve a preguntar al usuario.  
  
## Lista de inclusión y Windows Installer  
 Para instalar las soluciones de Office en el directorio Archivos de programa mediante Windows Installer, se requieren derechos de administrador. En cuanto a las soluciones de Office del directorio Archivos de programa, Visual Studio Tools para Office Runtime no comprueba la lista de inclusión debido a que las soluciones de Office ya poseen permisos FullTrust.  
  
## Solicitud de fiabilidad de ClickOnce  
 Si se usa la implementación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] para soluciones de Office, los administradores podrán configurar el nivel del mensaje de solicitud de fiabilidad para permitir que se realice la solicitud, para deshabilitarla o para solicitar un certificado de confianza. Esta configuración se realiza con una clave de registro que controla el acceso a la lista de inclusión.  
  
 Si se deshabilita la solicitud, sólo se pueden instalar las soluciones que dispongan de un certificado de confianza. Si el nivel de la solicitud se establece como “Authenticode necesario”, la solución se debe firmar con un certificado procedente de una autoridad conocida, pero no será necesario ningún certificado que vincule a una autoridad raíz de confianza \(es decir, un certificado de confianza\). Si se permite la solicitud, la solución se podrá firmar mediante un certificado cuya identidad sea desconocida. En este caso, la decisión de decidir si se confía en ese elemento o no, se deja al usuario final; es más, basta con un certificado temporal para instalar una solución.  
  
 Para obtener más información, consulte [Cómo: Configurar la seguridad de la lista de inclusión](../vsto/how-to-configure-inclusion-list-security.md) y la tabla 2 sobre los efectos que el nivel de solicitud de los valores de la clave de registro tienen en el inicio, en [Configurar los publicadores fiables de ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## Estructura de la lista de inclusión  
 Una entrada de lista de inclusión válida tiene dos partes: una ruta de acceso al manifiesto de implementación y la clave pública que se usa para firmar la solución. Una vez agregada una solución a la lista de inclusión, se considera de confianza. Cuando se ejecuta la solución de Office, la aplicación de Office compara la clave pública de la lista de inclusión con la clave de firma del manifiesto de implementación, para comprobar que la solución que se está ejecutando actualmente es igual que la versión de confianza original.  
  
## Vea también  
 [Otorgar confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)   
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)  
  
  