---
title: 'Cómo: crear asociaciones de archivo para una aplicación ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf60327e622f8eb32757d29051e3dce94661722d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Cómo: Crear asociaciones de archivo para una aplicación ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones se pueden asociadas con una o varias extensiones de nombre de archivo, para que la aplicación se iniciará automáticamente cuando el usuario abre un archivo de esos tipos. Agregar compatibilidad con extensiones de nombre de archivo a un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación es sencilla.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Para crear asociaciones de archivo para una aplicación ClickOnce  
  
1.  Crear un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación normalmente, o usar el existente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
2.  Abra el manifiesto de aplicación con un texto o editor XML, como el Bloc de notas.  
  
3.  Busque el elemento `assembly`. Para más información, consulte [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Como un elemento secundario de la `assembly` elemento, agregue un `fileAssociation` elemento. El `fileAssociation` elemento tiene cuatro atributos:  
  
    -   `extension`: La extensión de nombre de archivo que desea asociar a la aplicación.  
  
    -   `description`: Una descripción del tipo de archivo, que aparecerá en el shell de Windows.  
  
    -   `progid`: Una cadena que identifica de forma única el tipo de archivo, para marcar en el registro.  
  
    -   `defaultIcon`: Un icono que se utilizará para este tipo de archivo. El icono debe agregarse como un recurso de archivo en el manifiesto de aplicación. Para obtener más información, consulta [Cómo: Incluir un archivo de datos en una aplicación ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Para obtener un ejemplo de la `file` y `fileAssociation` elementos, consulte [ \<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Si desea asociar más de un tipo de archivo a la aplicación, agregar más `fileAssociation` elementos. Tenga en cuenta que el `progid` debe ser diferente para cada atributo.  
  
6.  Cuando haya terminado con el manifiesto de aplicación, volver a firmar el manifiesto. Puede hacerlo desde la línea de comandos mediante el uso de Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Para obtener más información, vea [Mage.exe (generación de manifiestos y herramienta de edición)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>Vea también  
 [\<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)