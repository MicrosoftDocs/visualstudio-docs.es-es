---
title: 'Cómo: incluir un archivo de datos en una aplicación ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ced10a16bae0e5892fddec1a79b9f7793b4dac43
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815550"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Cómo: Incluir un archivo de datos en una aplicación ClickOnce
Cada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que se instala se le asigna un directorio de datos en el disco local del equipo de destino donde la aplicación puede administrar sus propios datos. Archivos de datos pueden incluir archivos de cualquier tipo: archivos de texto, archivos XML o incluso archivos de base de datos (.mdb) de Microsoft Access. Los procedimientos siguientes muestran cómo agregar un archivo de datos de cualquier tipo en su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Para incluir un archivo de datos mediante Mage.exe  
  
1.  Agregar el archivo de datos a su directorio de aplicación con el resto de los archivos de la aplicación.  
  
     Normalmente, será el directorio de la aplicación a un directorio etiquetado con la versión actual de la implementación, por ejemplo, v1.0.0.0.  
  
2.  Actualizar el manifiesto de aplicación en el archivo de datos de la lista.  
  
     `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`  
  
     Realización de esta tarea vuelve a crea la lista de archivos en el manifiesto de aplicación y también genera automáticamente las firmas de hash.  
  
3.  Abra el manifiesto de aplicación en el editor XML o texto que prefiera y busque el `file` (elemento) para el archivo que se ha agregado.  
  
     Si ha agregado un archivo XML denominado `Data.xml`, el archivo tendrá un aspecto similar al ejemplo de código siguiente.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Agregue el atributo `type` a este elemento y suministrarlo con un valor de `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Volver a firmar el manifiesto de aplicación con el par de claves o un certificado y, a continuación, volver a firmar el manifiesto de implementación.  
  
     Debe volver a firmar el manifiesto de implementación porque el hash del manifiesto de aplicación ha cambiado.  
  
     `mage -s app manifest -cf cert_file -pwd password`
  
     `mage -u deployment manifest -appm app manifest`
  
     `mage -s deployment manifest -cf certfile -pwd password`
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Para incluir un archivo de datos mediante MageUI.exe  
  
1.  Agregar el archivo de datos a su directorio de aplicación con el resto de los archivos de la aplicación.  
  
2.  Normalmente, será el directorio de la aplicación a un directorio etiquetado con la versión actual de la implementación, por ejemplo, v1.0.0.0.  
  
3.  En el **archivo** menú, haga clic en **abrir** para abrir el manifiesto de aplicación.  
  
4.  Seleccione el **archivos** ficha.  
  
5.  En el cuadro de texto en la parte superior de la ficha, escriba el directorio que contiene los archivos de la aplicación y, a continuación, haga clic en **rellenar**.  
  
     El archivo de datos aparecerá en la cuadrícula.  
  
6.  Establecer el **tipo de archivo** valor del archivo de datos a **datos**.  
  
7.  Guarde el manifiesto de aplicación y, a continuación, volver a firmar el archivo.  
  
     MageUI.exe le pedirá que vuelva a firmar el archivo.  
  
8.  Volver a firmar el manifiesto de implementación  
  
     Debe volver a firmar el manifiesto de implementación porque el hash del manifiesto de aplicación ha cambiado.  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso local o remoto a los datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)