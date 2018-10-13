---
title: DisassemblyData | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dfbcdb4fdd9d356792b424d07f15c567d6e45624
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205782"
---
# <a name="disassemblydata"></a>DisassemblyData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Describe una instrucción de desensamblado para el entorno de desarrollo integrado (IDE) para mostrar.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
```csharp  
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
  
## <a name="members"></a>Miembros  
 `dwFields`  
 El [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) constante que especifica qué campos se rellenan.  
  
 `bstrAddress`  
 La dirección como un desplazamiento desde el punto de inicio (normalmente el principio de la función asociada).  
  
 `bstrCodeBytes`  
 Bytes de código para esta instrucción.  
  
 `bstrOpcode`  
 El código de operación para esta instrucción.  
  
 `bstrOperands`  
 Los operandos de esta instrucción.  
  
 `bstrSymbol`  
 El nombre del símbolo, si hay alguno, asociado con la dirección (símbolos públicos, etiqueta y así sucesivamente).  
  
 `uCodeLocationId`  
 El identificador de ubicación de código para esta línea de desensamblado. Si la dirección de contexto de código de una línea es mayor que la dirección de contexto de código de otro, el identificador de ubicación el código desensamblado del primer también será mayor que el identificador de ubicación del código de la segunda.  
  
 `posBeg`  
 El [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que corresponde a la posición de un documento donde comienzan los datos de desensamblado.  
  
 `posEnd`  
 El [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que corresponde a la posición de un documento que acaba de los datos de desensamblado.  
  
 `bstrDocumentUrl`  
 Para los documentos de texto que se pueden representar como nombres de archivo, el `bstrDocumentUrl` campo se rellena con el nombre de archivo donde se puede encontrar el origen, con el formato `file://file name`.  
  
 Para los documentos de texto que no se puede representar como nombres de archivo, `bstrDocumentUrl` es un identificador único para el documento y el motor de depuración debe implementar la [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) método.  
  
 Este campo puede contener también información adicional sobre las sumas de comprobación. Para obtener más información, vea la sección Comentarios.  
  
 `dwByteOffset`  
 El número de bytes de que la instrucción es desde el principio de la línea de código.  
  
 `dwFlags`  
 El [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) constante que especifica las marcas que están activas.  
  
## <a name="remarks"></a>Comentarios  
 Cada `DisassemblyData` estructura describe una instrucción de desensamblado. Una matriz de estas estructuras se devuelve desde el [lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.  
  
 El [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura se usa sólo en documentos basados en texto. El intervalo de código de origen para esta instrucción se rellena solo para la primera instrucción generada a partir de una instrucción o línea, por ejemplo, cuando `dwByteOffset == 0`.  
  
 Para los documentos que son no textuales, se puede obtener un contexto de documento desde el código y el `bstrDocumentUrl` campo debe ser un valor null. Si el `bstrDocumentUrl` campo es el mismo que el `bstrDocumentUrl` campo anterior `DisassemblyData` elemento de matriz, a continuación, establezca el `bstrDocumentUrl` con un valor null.  
  
 Si el `dwFlags` campo tiene la `DF_DOCUMENT_CHECKSUM` marcador establecido, a continuación, obtener información adicional de la suma de comprobación sigue a la cadena señalada por el `bstrDocumentUrl` campo. En concreto, después del terminador de cadena nula, sigue un GUID que identifica el algoritmo de suma de comprobación que a su vez está seguido por un valor de 4 bytes que indica el número de bytes de la suma de comprobación y que a su vez va seguido por los bytes de la suma de comprobación. Vea el ejemplo de este tema sobre cómo codificar y descodificar este campo en [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
## <a name="example"></a>Ejemplo  
 El `bstrDocumentUrl` campo puede contener información adicional que no sea una cadena si el `DF_DOCUMENT_CHECKSUM` marca está establecida. El proceso de creación y lectura de esta cadena codificada es sencillo en [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)]. Sin embargo, en [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], es otra cosa. Para aquellos que están curiosidad, en el ejemplo siguiente se muestra una forma de crear la cadena codificada de [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] y unidireccional para descodificar la cadena codificada en [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
```csharp  
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
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

