---
title: Conceder confianza a los documentos
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d245ddf00e4005b763bcd4437d3f8c18d05291e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986039"
---
# <a name="grant-trust-to-documents"></a>Conceder confianza a los documentos
  Un proyecto de nivel de documento tiene los mismos requisitos de seguridad que los proyectos de nivel de aplicación, esto es, firmar los manifiestos con un certificado o hacer clic en el aviso de confianza. Además, el documento o libro debe encontrarse en un directorio designado como ubicación de confianza.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="trusted-locations"></a>Ubicaciones de confianza
 Las aplicaciones de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y Office 2010 tienen centros de confianza en los que los usuarios pueden configurar las opciones de seguridad y privacidad, como las ubicaciones de confianza. En el caso de las soluciones de Office, el equipo local se considera una ubicación de confianza. Sin embargo, hay ciertos directorios que representan un riesgo más alto y que, por tanto, nunca pueden ser de confianza, como son las carpetas temporales del sistema, de cada usuario y de Internet Explorer.

 Para obtener más información sobre el centro de confianza, vea [seguridad y directivas y configuración en Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)). Para obtener más información acerca de cómo crear, administrar, quitar y configurar carpetas de confianza, vea [configurar ubicaciones de confianza y editores de confianza en el sistema de Office 2007](/previous-versions/office/office-2007-resource-kit/cc178948(v=office.12)) y [crear, quitar o cambiar una ubicación de confianza para los archivos](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="security-considerations-for-office-solutions"></a>Consideraciones de seguridad para las soluciones de Office
 Hay varias cuestiones de seguridad que se deben tener en cuenta al considerar las carpetas que desea agregar a las ubicaciones de confianza:

- Las carpetas locales se consideran más seguras y son de confianza de forma implícita. Las ubicaciones remotas, como recursos compartidos de archivos, deben designarse como ubicaciones de confianza.

- Al agregar un directorio a las ubicaciones de confianza, se concede plena confianza no sólo a las soluciones de Office, sino también al código de VBA y ActiveX. Por esta razón, el directorio raíz y las carpetas *Mis documentos* no deben designarse como de confianza.

- Aunque al utilizar las ubicaciones de confianza, el propio documento es de confianza, se necesitan permisos adicionales para confiar en la personalización. Puede conceder plena confianza a la personalización mediante la firma de los manifiestos con un certificado, haciendo clic en el mensaje de confianza o instalando la solución de Office en el directorio *archivos de programa* .

- Puede almacenar el documento o libro de una solución de nivel de documento en el mismo directorio que el ensamblado o en otro directorio. Por ejemplo, el documento podría estar ubicado en un servidor de SharePoint y el ensamblado en un recurso compartido de red. Para obtener más información, vea [Cómo: publicar una solución de Office de nivel de documento en un servidor de SharePoint mediante ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).

## <a name="see-also"></a>Consulte también
- [Conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)
- [Solucionar problemas de seguridad de soluciones de Office](../vsto/troubleshooting-office-solution-security.md)
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
