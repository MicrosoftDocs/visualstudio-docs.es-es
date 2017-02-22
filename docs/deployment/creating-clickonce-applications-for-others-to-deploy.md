---
title: "Crear aplicaciones ClickOnce para que las implementen terceros | Microsoft Docs"
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
  - "<useManifestForTrust> (elemento)"
  - "manifiestos de aplicación [ClickOnce]"
  - "aplicaciones ClickOnce, implementado por otros"
  - "aplicaciones ClickOnce, anteriores de .NET Framework"
  - "aplicaciones ClickOnce, versiones anteriores de .NET Framework"
  - "implementaciones por el cliente [ClickOnce]"
  - "manifiestos [ClickOnce]"
  - "marca comercial e implementaciones múltiples de ClickOnce"
  - "información de marca comercial conservada"
  - "aplicaciones de confianza, ClickOnce"
  - "useManifestForTrust (elemento)"
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Crear aplicaciones ClickOnce para que las implementen terceros
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No todos los programadores que crean implementaciones ClickOnce pretenden implementar las aplicaciones ellos mismos.  Muchos de ellos simplemente empaquetan la aplicación utilizando ClickOnce y, a continuación, entregan los archivos a un cliente como, por ejemplo, una gran corporación.  El cliente se convierte en el único responsable de hospedar la aplicación en su red.  En este tema se explican algunos de los problemas inherentes a este tipo de implementaciones en versiones de .NET anteriores a la 3.5.  A continuación, se describe una nueva solución que se proporciona mediante la nueva característica "utilizar manifiesto para confianza" de .NET Framework 3.5.  Por último, el tema concluye con las estrategias recomendadas para crear implementaciones ClickOnce destinadas a clientes que siguen usando versiones anteriores de .NET Framework.  
  
## Problemas relacionados con la creación de implementaciones para clientes  
 Cuando se planea suministrar una implementación a un cliente, surgen diversos problemas.  El primer problema tiene que ver con la firma de código.  Para poder implementarse en una red, tanto el manifiesto de implementación como el manifiesto de aplicación de una implementación ClickOnce deben estar firmados con un certificado digital.  Esto plantea la cuestión de si debe utilizarse el certificado del programador o del cliente a la hora de firmar los manifiestos.  
  
 La cuestión de qué certificado debe utilizarse en la firma es crucial, ya que la identidad de la aplicación ClickOnce se basa en la firma digital del manifiesto de implementación.  En caso de que el programador firme el manifiesto de implementación, pueden producirse conflictos si el cliente es una empresa de gran tamaño y varias de sus divisiones implementen una versión personalizada de la aplicación.  
  
 Por ejemplo, supongamos que Adventure Works tiene un departamento financiero y un departamento de recursos humanos.  Ambos departamentos otorgan licencias a una aplicación ClickOnce de Microsoft Corporation que genera informes de los datos almacenados en una base de datos SQL.  Microsoft proporciona a cada departamento una versión de la aplicación que se personaliza conforme a sus datos.  Si las aplicaciones se firman con el mismo certificado Authenticode, un usuario que intente utilizar ambas aplicaciones podría encontrar un error, ya que ClickOnce consideraría la segunda aplicación idéntica a la primera.  En este caso, el cliente podría experimentar efectos secundarios imprevisibles y no deseados, como la pérdida de algunos de los datos almacenados localmente por la aplicación.  
  
 Un problema adicional relacionado con la firma de código es el elemento `deploymentProvider` del manifiesto de implementación, que indica a ClickOnce dónde debe buscar las actualizaciones de la aplicación.  Este elemento tiene que agregarse al manifiesto de implementación previamente a la firma del mismo.  Si este elemento se agregara después, debería volver a firmarse el manifiesto de implementación.  
  
### Solicitar al cliente que firme el manifiesto de implementación  
 Una solución a este problema de implementaciones que no son únicas es hacer que el programador firme el manifiesto de aplicación y que el cliente firme el manifiesto de implementación.  Aunque este enfoque funciona, presenta otra serie de problemas.  Como los certificados Authenticode deben seguir siendo un activo protegido, el cliente no puede simplemente dar el certificado al programador para que firme la implementación.  Aunque el cliente puede firmar el manifiesto de implementación por sí mismo utilizando las herramientas disponibles de forma gratuita en .NET Framework SDK, esto puede requerir un mayor conocimiento técnico del que el cliente está dispuesto a proporcionar o es capaz de proporcionar.  En casos de este tipo, el programador suele crear una aplicación, un sitio web u otro mecanismo a través del cual el cliente puede enviar su versión de la aplicación para que se firme.  
  
### Impacto de la firma del cliente en la seguridad de la aplicación ClickOnce  
 Aunque el programador y el cliente estén de acuerdo en que debe ser el cliente el que firme el manifiesto de aplicación, esto da lugar a otros problemas en relación con la identidad de la aplicación, en especial cuando se trata de la implementación de aplicaciones de confianza.  \(Para obtener más información acerca de esta característica, vea [Información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).\) Supongamos que Adventure Works desea configurar sus equipos cliente para que cualquier aplicación que le proporcione Microsoft Corporation se ejecute con plena confianza.  Si Adventure Works firma el manifiesto de implementación, ClickOnce usará la firma de seguridad de Adventure Works para determinar el nivel de confianza de la aplicación.  
  
## Crear implementaciones de cliente usando el manifiesto de aplicación para confianza  
 En .NET Framework 3.5, ClickOnce incluye una nueva característica que proporciona a los programadores y a los clientes una solución al problema de cómo deben firmarse los manifiestos.  El manifiesto de aplicación ClickOnce admite un nuevo elemento denominado `<useManifestForTrust>` que permite que el programador indique que la firma digital del manifiesto de aplicación es la que debe utilizarse para tomar decisiones relacionadas con la confianza.  El programador usa las herramientas de empaquetado de ClickOnce, como Mage.exe, MageUI.exe y Visual Studio, para incluir este elemento en el manifiesto de aplicación, así como para incrustar el nombre del publicador y el nombre de la aplicación en el manifiesto.  
  
 Cuando se usa el elemento `<useManifestForTrust>`, el manifiesto de implementación no tiene que estar firmado con un certificado Authenticode emitido por una entidad de certificación.  En lugar de ello, puede estar firmado con lo que se conoce como un certificado autofirmado.  El cliente o el programador genera un certificado autofirmado utilizando las herramientas estándar de .NET Framework SDK y, a continuación, se lo aplica al manifiesto de implementación utilizando las herramientas de implementación estándar de ClickOnce.  Para obtener más información, consulte [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md).  
  
 El uso de un certificado autofirmado en el manifiesto de implementación presenta una serie de ventajas.  Al eliminar la necesidad de que el cliente obtenga o cree su propio certificado Authenticode, el elemento `<useManifestForTrust>` simplifica la implementación para el cliente, al mismo tiempo que permite al programador mantener su propia identidad de marca en la aplicación.  El resultado es un conjunto de implementaciones firmadas que son más seguras y que tienen identidades de aplicación únicas.  Esto elimina el posible conflicto que puede producirse al implementar la misma aplicación para varios clientes.  
  
 Para obtener información paso a paso acerca de cómo crear una implementación ClickOnce con la característica `<useManifestForTrust>` habilitada, vea [Tutorial: Implementar manualmente una aplicación ClickOnce que no requiera el proceso de volver a firmar y que conserve la información de marca comercial](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### Cómo funciona el manifiesto de aplicación para confianza en tiempo de ejecución  
 Para entender mejor cómo funciona el manifiesto de aplicación para confianza en tiempo de ejecución, observe el siguiente ejemplo.  Microsoft crea una aplicación ClickOnce destinada a .NET Framework 3.5.  El manifiesto de aplicación usa el elemento `<useManifestForTrust>` y está firmado por Microsoft.  Adventure Works firma el manifiesto de implementación utilizando un certificado autofirmado.  Los clientes de Adventure Works se configuran de modo que confíen en cualquier aplicación firmada por Microsoft.  
  
 Cuando un usuario hace clic en un vínculo al manifiesto de implementación, ClickOnce instala la aplicación en el equipo del usuario.  El certificado y la información de implementación hacen que ClickOnce identifique de forma única la aplicación en el equipo cliente.  Si el usuario intenta volver a instalar la misma aplicación desde una ubicación diferente, ClickOnce puede usar esta identidad para determinar si la aplicación ya existe en el cliente.  
  
 A continuación, ClickOnce examina el certificado Authenticode que se usa para firmar el manifiesto de aplicación, que determina el nivel de confianza que ClickOnce concederá.  Puesto que Adventure Works ha configurado sus clientes para que confíen en cualquier aplicación firmada por Microsoft, a esta aplicación ClickOnce se le concede plena confianza.  Para obtener más información, vea [Información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).  
  
## Crear implementaciones de clientes para versiones anteriores  
 ¿Qué ocurre si un programador está implementando aplicaciones ClickOnce para clientes que usan versiones anteriores de .NET Framework?  En las secciones siguientes se resumen varias de las soluciones recomendadas, así como las ventajas e inconvenientes de cada una de ellas.  
  
### Firmar implementaciones en nombre del cliente  
 Una posible estrategia de implementación es que el programador cree un mecanismo para firmar las implementaciones en nombre de sus clientes usando la clave privada del cliente.  De este modo, se evita que el programador tenga que administrar claves privadas o varios paquetes de implementación.  El programador se limita a proporcionar la misma implementación a cada cliente.  Es responsabilidad del cliente personalizar la aplicación en función de su entorno mediante el servicio de firma.  
  
 Uno de los inconvenientes de este método es el tiempo y los gastos que se invierten en la implementación.  Aunque este tipo de servicio puede compilarse con las herramientas que se incluyen en .NET Framework SDK, agregará más tiempo de implementación al ciclo de vida del producto.  
  
 Tal y como se ha indicado anteriormente en este tema, otro de los inconvenientes es que la versión de la aplicación de cada cliente tendrá la misma identidad de aplicación, lo que puede generar conflictos.  Si esto supone un problema, el programador puede cambiar el campo Nombre que se utiliza al generar el manifiesto de implementación para asignar un nombre único a cada aplicación.  Esto hará que se cree una identidad diferente para cada versión de la aplicación y eliminará cualquier posible conflicto de identidad.  Este campo se corresponde con el argumento `-Name` en Mage.exe y con el campo **Nombre** de la ficha **Nombre** en MageUI.exe.  
  
 Por ejemplo, supongamos que el programador ha creado una aplicación denominada Aplicación1.  En lugar de crear una sola implementación con el campo Nombre establecido en Aplicación1, el programador puede crear varias implementaciones cambiando el nombre para cada cliente como, por ejemplo, Aplicación1\-ClienteA, Aplicación1\-ClienteB, etc.  
  
### Implementar mediante un paquete de instalación  
 Otra estrategia de implementación posible consiste en generar un proyecto de instalación de Microsoft para realizar la implementación inicial de la aplicación ClickOnce.  Este proyecto puede presentarse en distintos formatos, como una implementación MSI, un archivo ejecutable de instalación \(.EXE\) o un archivo contenedor \(.cab\) junto con un script por lotes.  
  
 Con esta técnica, el programador podría proporcionar al cliente una implementación con los archivos de la aplicación, el manifiesto de aplicación y un manifiesto de implementación que actuaría como una plantilla.  El cliente ejecutaría el programa de instalación, que solicitaría a los usuarios una dirección URL de implementación \(la ubicación del servidor o de un recurso compartido de archivos desde la que los usuarios instalarán la aplicación ClickOnce\), así como un certificado digital.  La aplicación de instalación también podría solicitar opciones de configuración de ClickOnce adicionales, como un intervalo de comprobación de actualizaciones.  Una vez recopilada esta información, el programa de instalación generaría el manifiesto de implementación real, lo firmaría y publicaría la aplicación ClickOnce en la ubicación designada del servidor.  
  
 En una situación de este tipo, el cliente podría firmar el manifiesto de implementación de tres modos diferentes:  
  
1.  El cliente puede utilizar un certificado válido emitido por una entidad de certificación \(CA\).  
  
2.  Como variación a este enfoque, el cliente puede optar por firmar su manifiesto de implementación con un certificado autofirmado.  El inconveniente de esto último es que la aplicación mostrará las palabras "Publicador desconocido" cuando se pregunte al usuario si desea instalar la aplicación.  Sin embargo, tiene la ventaja de que se evita que los clientes más pequeños tengan que invertir el tiempo y dinero necesarios para obtener un certificado emitido por una entidad de certificación.  
  
3.  Finalmente, el programador puede incluir su propio certificado autofirmado en el paquete de instalación.  Esto podría generar los problemas explicados anteriormente en este tema relativos a la identidad de las aplicaciones.  
  
 El inconveniente que presenta el método del proyecto de implementación de instalación es el tiempo y los gastos necesarios para compilar una aplicación de implementación personalizada.  
  
### Hacer que el cliente genere el manifiesto de implementación  
 Una tercera estrategia de implementación posible consiste en entregar los archivos y el manifiesto de la aplicación al cliente.  En este caso, el usuario es el responsable de utilizar .NET Framework SDK para generar y firmar el manifiesto de implementación.  
  
 El inconveniente de este método es que obliga al cliente a instalar las herramientas de .NET Framework SDK y que exige que el cliente tenga un programador o administrador del sistema con experiencia en su uso.  Algunos clientes pueden demandar una solución que requiera poco esfuerzo técnico por su parte o ninguno en absoluto.  
  
## Vea también  
 [Implementar aplicaciones ClickOnce para los servidores de pruebas y producción sin nueva firma](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Tutorial: Implementar manualmente una aplicación ClickOnce que no requiera el proceso de volver a firmar y que conserve la información de marca comercial](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)