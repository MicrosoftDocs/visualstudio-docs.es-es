---
title: Incluir un archivo de datos en una aplicación ClickOnce
description: Obtenga información acerca de cómo agregar un archivo de datos de cualquier tipo en la aplicación ClickOnce para almacenarlo en un directorio de datos en el disco local del equipo de destino.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f4b5e8fe9d17a6de9abac2681074dcfc162e9b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900604"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Cómo: Incluir un archivo de datos en una aplicación ClickOnce
A cada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que se instala se le asigna un directorio de datos en el disco local del equipo de destino, donde la aplicación puede administrar sus propios datos. Los archivos de datos pueden incluir archivos de cualquier tipo: archivos de texto, archivos XML o incluso archivos de base de datos de Microsoft Access (*. mdb*). En los procedimientos siguientes se muestra cómo agregar un archivo de datos de cualquier tipo a la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.

### <a name="to-include-a-data-file-by-using-mageexe"></a>Para incluir un archivo de datos mediante Mage.exe

1. Agregue el archivo de datos al directorio de la aplicación con el resto de los archivos de la aplicación.

    Normalmente, el directorio de la aplicación será un directorio con la etiqueta de la versión actual de la implementación, por ejemplo, v 1.0.0.0.

2. Actualice el manifiesto de aplicación para mostrar el archivo de datos.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    Al realizar esta tarea, se vuelve a crear la lista de archivos en el manifiesto de aplicación y también se generan automáticamente las firmas hash.

3. Abra el manifiesto de aplicación en el editor XML o de texto que prefiera y busque el `file` elemento del archivo agregado recientemente.

    Si agregó un archivo XML denominado `Data.xml` , el archivo tendrá un aspecto similar al siguiente ejemplo de código.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. Agregue el atributo `type` a este elemento y proporcione un valor de `data` .

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Vuelva a firmar el manifiesto de aplicación con el certificado o el par de claves y, a continuación, vuelva a firmar el manifiesto de implementación.

    Debe volver a firmar el manifiesto de implementación porque el hash del manifiesto de aplicación ha cambiado.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Para incluir un archivo de datos mediante MageUI.exe

1. Agregue el archivo de datos al directorio de la aplicación con el resto de los archivos de la aplicación.

2. Normalmente, el directorio de la aplicación será un directorio con la etiqueta de la versión actual de la implementación, por ejemplo, v 1.0.0.0.

3. En el menú **archivo** , haga clic en **abrir** para abrir el manifiesto de aplicación.

4. Seleccione la pestaña **archivos** .

5. En el cuadro de texto de la parte superior de la pestaña, escriba el directorio que contiene los archivos de la aplicación y, a continuación, haga clic en **rellenar**.

     El archivo de datos aparecerá en la cuadrícula.

6. Establezca el valor de **tipo de archivo** del archivo de datos en **Data**.

7. Guarde el manifiesto de aplicación y, a continuación, vuelva a firmar el archivo.

     *MageUI.exe* le pedirá que vuelva a firmar el archivo.

8. Volver a firmar el manifiesto de implementación

     Debe volver a firmar el manifiesto de implementación porque el hash del manifiesto de aplicación ha cambiado.

## <a name="see-also"></a>Vea también
- [Acceso a datos locales y remotos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)