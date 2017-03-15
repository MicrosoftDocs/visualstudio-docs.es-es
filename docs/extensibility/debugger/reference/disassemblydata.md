---
title: "DisassemblyData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DisassemblyData"
helpviewer_keywords: 
  - "DisassemblyData (estructura)"
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# DisassemblyData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Describe una instrucción de desensamblado del entorno de desarrollo \(IDE\) integrado en la pantalla.  
  
## Sintaxis  
  
```cpp#  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```c#  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## Members  
 `dwFields`  
 La constante de [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) que especifica se completan los campos.  
  
 `bstrAddress`  
 La dirección como un desplazamiento de algún punto inicial \(normalmente el principio de la función asociada\).  
  
 `bstrCodeBytes`  
 Los bytes de código para esta instrucción.  
  
 `bstrOpcode`  
 el código de operación para esta instrucción.  
  
 `bstrOperands`  
 los operandos para esta instrucción.  
  
 `bstrSymbol`  
 El nombre de símbolo, si existe, asociado con la dirección \(símbolo, etiqueta públicos, etc.\).  
  
 `uCodeLocationId`  
 El identificador de la ubicación del código para esta línea desensamblada.  Si la dirección del contexto del código de una línea es mayor que la dirección del contexto del código de otra, el identificador desensamblado de la ubicación del código del primer también será mayor que el identificador de la ubicación del código del segundo.  
  
 `posBeg`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) que corresponde a la posición en un documento en el que comienza el datos de desensamblado.  
  
 `posEnd`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) que corresponde a la posición en un documento cuyos datos de desensamblado finaliza.  
  
 `bstrDocumentUrl`  
 Para los documentos de texto que se puede representar como nombres de archivo, el campo de `bstrDocumentUrl` se completa con el nombre de archivo en el origen se encuentra, con el formato `nombre de file://file`.  
  
 Para los documentos de texto que no se pueden representar como nombres de archivo, `bstrDocumentUrl` es un identificador único para el documento, y el motor de depuración debe implementar el método de [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) .  
  
 Este campo también puede contener información adicional sobre sumas de comprobación.  Vea las notas de detalles.  
  
 `dwByteOffset`  
 El número de bytes la instrucción se desde el principio de la línea de código.  
  
 `dwFlags`  
 La constante de [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) que especifica que los marcadores están activas.  
  
## Comentarios  
 Cada estructura de `DisassemblyData` describe una instrucción de desensamblado.  Una matriz de estas estructuras se devuelve del método de [Leer](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .  
  
 La estructura de [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) se utiliza para los documentos basados en texto.  El intervalo de código fuente para esta instrucción se completa solo para la primera instrucción generada de una instrucción o una línea; por ejemplo, si `dwByteOffset == 0`.  
  
 Para los documentos que son no textuales, un contexto de documento se puede obtener de código, y el campo de `bstrDocumentUrl` debe ser un valor NULL.  Si el campo de `bstrDocumentUrl` es igual que el campo de `bstrDocumentUrl` en el elemento de matriz anterior de `DisassemblyData` , establezca `bstrDocumentUrl` en un valor nulo.  
  
 Si el campo de `dwFlags` tiene el indicador de `DF_DOCUMENT_CHECKSUM` establecido, la información de suma de comprobación adicional sigue la cadena indicada por el campo de `bstrDocumentUrl` .  Específicamente, después del terminador de la cadena nula, sigue un GUID que identifica el algoritmo de suma de comprobación que a su vez va seguido de un valor de 4 bytes que indica el número de bytes de la suma de comprobación y que a su vez sigue los bytes de la suma de comprobación.  Vea el ejemplo de este tema en cómo codificar y descodificar este campo en [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
## Ejemplo  
 El campo de `bstrDocumentUrl` puede contener información adicional que no sea una cadena si se establece la marca de `DF_DOCUMENT_CHECKSUM` .  El proceso de crear y leer esta cadena codificada es sencillo en [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)].  Sin embargo, en [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)], es otra asunto.  Para los que se curiosos, el ejemplo siguiente muestra una manera de crear la cadena codificada de [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] y una forma de descodificar la cadena codificada en [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
```c#  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Leer](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)