---
title: Conceder confianza a documentos
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f95887d5d540fd1acd95b8af1275c4b4054c8764
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="grant-trust-to-documents"></a>Conceder confianza a documentos
  Un proyecto de nivel de documento tiene los mismos requisitos de seguridad que los proyectos de nivel de aplicación, esto es, firmar los manifiestos con un certificado o hacer clic en el aviso de confianza. Además, el documento o libro debe encontrarse en un directorio designado como ubicación de confianza.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Ubicaciones de confianza  
 Las aplicaciones de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y Office 2010 disponen de centros de confianza donde los usuarios pueden configurar la configuración de seguridad y privacidad, como ubicaciones de confianza. Para las soluciones de Office, el equipo local se considera una ubicación de confianza. Sin embargo, hay ciertos directorios que representan un riesgo más alto y que, por tanto, nunca pueden ser de confianza, como son las carpetas temporales del sistema, de cada usuario y de Internet Explorer.  
  
 Para obtener más información sobre el centro de confianza, consulte [ajustes en Office 2010 y las directivas de seguridad](http://go.microsoft.com/fwlink/?LinkId=89202). Para obtener más información acerca de cómo crear, administrar, quitar y configurar carpetas de confianza, consulte [configurar ubicaciones de confianza y opciones de editores de confianza en 2007 Office system](http://go.microsoft.com/fwlink/?LinkId=89203) y [crear, quitar o cambiar un ubicación de los archivos de confianza](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Consideraciones de seguridad para soluciones de Office  
 Hay varias cuestiones de seguridad que se deben tener en cuenta al considerar las carpetas que desea agregar a las ubicaciones de confianza:  
  
-   Las carpetas locales se consideran más seguras y son de confianza de forma implícita. Las ubicaciones remotas, como recursos compartidos de archivos, deben designarse como ubicaciones de confianza.  
  
-   Al agregar un directorio a las ubicaciones de confianza, se concede plena confianza no sólo a las soluciones de Office, sino también al código de VBA y ActiveX. Por esta razón, el directorio raíz y el *Mis documentos* carpetas no deben designarse como de confianza.  
  
-   Aunque al utilizar las ubicaciones de confianza, el propio documento es de confianza, se necesitan permisos adicionales para confiar en la personalización. Puede conceder plena confianza a la personalización mediante firmar los manifiestos con un certificado, haga clic en el aviso de confianza o instalar la solución de Office para la *archivos de programa* directory.  
  
-   Puede almacenar el documento o libro de una solución de nivel de documento en el mismo directorio que el ensamblado o en otro directorio. Por ejemplo, el documento podría estar ubicado en un servidor de SharePoint y el ensamblado en un recurso compartido de red. Para obtener más información, consulte [Cómo: publicar una solución de Office de nivel de documento en un servidor de SharePoint mediante ClickOnce](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Vea también  
 [Conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)   
 [Solucionar problemas de seguridad de la solución de Office](../vsto/troubleshooting-office-solution-security.md)   
 [Proteger soluciones de Office](../vsto/securing-office-solutions.md)  
  
  