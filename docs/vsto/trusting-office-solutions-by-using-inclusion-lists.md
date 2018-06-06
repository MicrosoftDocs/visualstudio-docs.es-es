---
title: Confiar en soluciones de Office mediante listas de inclusión
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6fb44e7927136ba02d04f4b57f38ae52cc76c9fd
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767889"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Confiar en soluciones de Office mediante listas de inclusión
  Las listas de inclusión permiten a los usuarios decidir si las soluciones de Office firmadas con un certificado que identifique al publicador son fiables. Las listas de inclusión son específicas del usuario y se pueden usar en las personalizaciones de nivel de documento y en los complementos VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Cuando un usuario inicia una solución de Office que no se haya indicado como fiable, la solución de Microsoft Office le solicita que confirme si confía en esa solución mediante una pregunta de seguridad de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Si el usuario decide que la solución es fiable, la personalización se ejecuta y no se vuelve a preguntar al usuario.  
  
## <a name="inclusion-list-and-windows-installer"></a>Lista de inclusión y Windows Installer  
 Para instalar las soluciones de Office en el directorio Archivos de programa mediante Windows Installer, se requieren derechos de administrador. Para las soluciones de Office en el directorio de archivos de programa, Visual Studio Tools para Office runtime no comprueba la lista de inclusión porque ya se han otorgado permisos FullTrust a las soluciones de Office.  
  
## <a name="clickonce-trust-prompt"></a>Aviso de confianza de ClickOnce  
 Si se usa la implementación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] para soluciones de Office, los administradores podrán configurar el nivel del mensaje de solicitud de fiabilidad para permitir que se realice la solicitud, para deshabilitarla o para solicitar un certificado de confianza. Esta configuración se realiza con una clave de registro que controla el acceso a la lista de inclusión.  
  
 Si se deshabilita la solicitud, sólo se pueden instalar las soluciones que dispongan de un certificado de confianza. Si el nivel de la solicitud se establece como “Authenticode necesario”, la solución se debe firmar con un certificado procedente de una autoridad conocida, pero no será necesario ningún certificado que vincule a una autoridad raíz de confianza (es decir, un certificado de confianza). Si se permite la solicitud, la solución se podrá firmar mediante un certificado cuya identidad sea desconocida. En este caso, la decisión de decidir si se confía en ese elemento o no, se deja al usuario final; es más, basta con un certificado temporal para instalar una solución.  
  
 Para obtener más información, consulte [Cómo: configurar la seguridad de la lista de inclusión](../vsto/how-to-configure-inclusion-list-security.md) y la tabla 2, titulada preguntar nivel del registro clave valor efectos del inicio en [editores de confianza de ClickOnce configurar](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="structure-of-the-inclusion-list"></a>Estructura de la lista de inclusión  
 Una entrada de lista de inclusión válida tiene dos partes: una ruta de acceso al manifiesto de implementación y la clave pública que se usa para firmar la solución. Una vez agregada una solución a la lista de inclusión, se considera de confianza. Cuando se ejecuta la solución de Office, la aplicación de Office compara la clave pública de la lista de inclusión con la clave de firma del manifiesto de implementación, para comprobar que la solución que se está ejecutando actualmente es igual que la versión de confianza original.  
  
## <a name="see-also"></a>Vea también  
 [Conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)   
 [Proteger soluciones de Office](../vsto/securing-office-solutions.md)  
  
  