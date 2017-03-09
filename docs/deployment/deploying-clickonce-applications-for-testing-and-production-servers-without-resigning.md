---
title: "Implementar aplicaciones ClickOnce para los servidores de pruebas y producci&#243;n sin nueva firma | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "actualizaciones de aplicaciones, ClickOnce"
  - "aplicaciones ClickOnce, implementar sin nueva firma"
  - "implementación ClickOnce, sin nueva firma"
  - "deploymentProvider (etiqueta)"
  - "manifiestos [ClickOnce]"
  - "actualizar ubicación [ClickOnce]"
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implementar aplicaciones ClickOnce para los servidores de pruebas y producci&#243;n sin nueva firma
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describe una nueva característica de ClickOnce introducida en la versión 3.5 de .NET Framework que habilita la implementación de aplicaciones ClickOnce desde varias ubicaciones de red sin volver a firmar ni cambiar los manifiestos de ClickOnce.  
  
> [!NOTE]
>  Volver a firmar sigue siendo el método recomendado para implementar nuevas versiones de las aplicaciones.  Siempre que sea posible, utilice el método de volver a firmar.  Para obtener más información, vea [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
 Los programadores e ISV de terceros pueden adoptar esta característica, que permite que sus clientes actualicen fácilmente sus aplicaciones.  Esta característica se puede utilizar en las situaciones siguientes:  
  
-   Al actualizar una aplicación, no en la primera instalación de una aplicación.  
  
-   Cuando sólo hay una configuración de la aplicación en un equipo.  Por ejemplo, si una aplicación se configura para señalar a dos bases de datos diferentes, no se puede utilizar esta característica.  
  
## Excluir deploymentProvider de los manifiestos de implementación  
 En .NET Framework 2.0 y .NET Framework 3.0, las aplicaciones ClickOnce que se instalan en el sistema para disponibilidad sin conexión deben especificar `deploymentProvider` en su manifiesto de implementación.  `deploymentProvider` se suele denominar ubicación de actualización; es la ubicación en la que ClickOnce comprobará si hay actualizaciones de la aplicación.  Este requisito, junto con la necesidad de que los editores de aplicaciones firmen sus implementaciones, dificulta que una empresa actualice una aplicación ClickOnce de un proveedor u otro fabricante.  También dificulta la implementación de la misma aplicación procedente de varias ubicaciones en la misma red.  
  
 Con los cambios realizados a ClickOnce en .NET Framework 3.5, otros proveedores pueden proporcionar una aplicación ClickOnce a otra organización que, a continuación, puede implementarla en su propia red.  
  
 Para aprovechar las ventajas de esta característica, los programadores de aplicaciones ClickOnce deben excluir `deploymentProvider` de sus manifiestos de implementación.  Esto significa excluir el argumento `-providerUrl` al crear los manifiestos de implementación con Mage.exe, o asegurarse de que el cuadro de texto **Ubicación de inicio** en la ficha **Manifiesto de aplicación** está en blanco si va a generar los manifiestos de implementación con MageUI.exe.  
  
## deploymentProvider y actualizaciones de aplicaciones  
 A partir de .NET Framework 3.5, ya no es necesario especificar `deploymentProvider` en un manifiesto de implementación para implementar una aplicación ClickOnce tanto para su uso en línea como sin conexión.  Esto permite escenarios donde deba empaquetar y firmar la implementación personalmente pero que sean otras empresas las que implementen la aplicación en sus redes.  
  
 El punto clave para recordar es que las aplicaciones que excluyen `deploymentProvider` no pueden cambiar su ubicación de instalación durante las actualizaciones, hasta que distribuyan una actualización que incluya de nuevo la etiqueta `deploymentProvider`.  
  
 Éstos son dos ejemplos que aclararán este punto.  En el primer ejemplo, se publica una aplicación ClickOnce que no tiene ninguna etiqueta `deploymentProvider` y se pide a los usuarios que lo instalen desde http:\/\/www.adatum.com\/MyApplication\/.  Si decide que desea publicar la próxima actualización de la aplicación en http:\/\/subdomain.adatum.com\/MyApplication\/, no tendrá ninguna manera de indicarlo en el manifiesto de implementación ubicado en http:\/\/www.adatum.com\/MyApplication\/.  Puede hacer una de las dos cosas siguientes:  
  
-   Indique a sus usuarios que desinstalen la versión anterior e instalen la nueva versión desde la nueva ubicación.  
  
-   Incluya una actualización en http:\/\/www.adatum.com\/MyApplication\/ que contenga un `deploymentProvider` que señale a http:\/\/www.adatum.com\/MyApplication\/.  A continuación, publique otra actualización con `deploymentProvider` señalando a http:\/\/subdomain.adatum.com\/MyApplication\/.  
  
 En el segundo ejemplo, se publica una aplicación ClickOnce que especifica `deploymentProvider` y después decide quitarlo.  Una vez descargada a los clientes la nueva versión sin `deploymentProvider`, no podrá redirigir la ruta de acceso utilizada para las actualizaciones hasta que publique una versión de su aplicación con el valor de `deploymentProvider` restaurado.  Como en el primer ejemplo, `deploymentProvider` debe señalar inicialmente a la ubicación de actualización actual, no a la nueva ubicación.  En este caso, si intenta insertar un `deploymentProvider` que hace referencia a http:\/\/subdomain.adatum.com\/MyApplication\/, se producirá un error en la siguiente actualización.  
  
## Crear una implementación  
 Para obtener instrucciones paso a paso para crear implementaciones que se puedan implementar desde ubicaciones de red diferentes, vea [Tutorial: Implementar manualmente una aplicación ClickOnce que no requiera el proceso de volver a firmar y que conserve la información de marca comercial](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## Vea también  
 [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)