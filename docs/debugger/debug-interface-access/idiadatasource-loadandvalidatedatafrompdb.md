---
title: "IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "IDiaDataSource::loadAndValidateDataFromPdb (método)"
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abra y compruebe que coincida con el archivo de base de datos de programa \(.pdb\) la información de firma proporciona, y prepara el archivo .pdb como origen de datos de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### Parámetros  
 `pdbPath`  
 \[in\]  La ruta de acceso al archivo .pdb.  
  
 `pcsig70`  
 \[in\]  La firma de GUID a comprobar la firma del archivo .pdb.  Sólo los archivos .pdb en [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] y tienen más adelante firmas de GUID.  
  
 `sig`  
 \[in\]  La firma de 32 bits a comprobar la firma del archivo .pdb.  
  
 `age`  
 \[in\]  Valor de age a comprobar.  La edad no corresponde necesariamente ningún valor de tiempo conocido, se utiliza para determinar si un archivo .pdb está sincronizada con un archivo correspondiente .exe.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  la tabla siguiente muestra los valores devueltos posibles para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E\_PDB\_NOT\_FOUND|Error al abrir el archivo, o el archivo tiene un formato no válido.|  
|E\_PDB\_FORMAT|Ha intentado obtener acceso a un archivo con un formato obsoleto.|  
|E\_PDB\_INVALID\_SIG|la firma no coincide.|  
|E\_PDB\_INVALID\_AGE|la edad no coincide.|  
|E\_INVALIDARG|Parámetro no válido.|  
|E\_UNEXPECTED|el origen de datos se ha preparado ya.|  
  
## Comentarios  
 Un archivo .pdb contiene la firma y valores de edad.  Estos valores se replican en el archivo .exe o .dll que coincida con el archivo .pdb.  Antes de preparar el origen de datos, este método comprueba si la firma del archivo denominado .pdb y la coincidencia de edad que los valores proporcionados.  
  
 Para cargar un archivo .pdb sin validación, use el método de [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Para obtener acceso al proceso de carga de datos \(a través de un mecanismo de devolución de llamada\), utilice el método de [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
 Para cargar un archivo .pdb directamente de la memoria, utilice el método de [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .  
  
## Ejemplo  
  
```cpp#  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)