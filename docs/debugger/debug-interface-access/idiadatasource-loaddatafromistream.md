---
title: "IDiaDataSource::loadDataFromIStream | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::loadDataFromIStream (método)"
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Prepara los datos de depuración almacenados en un archivo de base de datos de programa \(.pdb\) tiene acceso mediante un flujo de datos en memoria.  
  
## Sintaxis  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### Parámetros  
 pIStream  
 \[in\]  Un objeto de <xref:IStream> que representa la secuencia de datos para utilizarlos.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  la tabla siguiente muestra los valores devueltos posibles para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E\_PDB\_FORMAT|Ha intentado obtener acceso a un archivo con un formato obsoleto.|  
|E\_INVALIDARG|Invalidparameter.|  
|E\_UNEXPECTED|el origen de datos se ha preparado ya.|  
  
## Comentarios  
 Este método permite que los datos de depuración para que una aplicación ejecutable sea obtenida de memoria entre un objeto de <xref:IStream> .  
  
 Para cargar un archivo .pdb sin validación, use el método de [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Para validar el archivo .pdb con los criterios específicos, utilice el método de [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Para obtener acceso al proceso de carga de datos \(a través de un mecanismo de devolución de llamada\), utilice el método de [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)