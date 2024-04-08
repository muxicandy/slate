---
title: uxc v1.0.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
code_clipboard: true
highlight_theme: darkula
headingLevel: 2
generator: "@tarslib/widdershins v4.0.11"

---

# uxc

> v1.0.0

# 工作台

## POST 获取任务结果

POST /api/dispatch/task/get

# 申请 Access Key 和 Secret Key

若需申请 AK 和 SK，需要按照以下步骤操作：

## 步骤 1：发送邮件

业务方首先需要发送邮件到 `uxc-aigc.zuoyebang.com` ，邮件内容需要包含以下信息:

- **业务方名称**：例如：`poly-app`
- **申请原因**：例如：接入UXC能力
- **预计任务量**：例如：`1000/天`
- **调用时段**：例如：`24:00-次日09:00`

请务必确保邮件内容的准确性和完整性。

## 步骤 2：联系管理员（伍思磊|严军05|熊英越|李阳阳06）

接着，联系 UX 管理员确认申请。请及时跟进并确保管理员已收到并处理了你的请求。

如果有任何问题或疑惑，都可以联系管理员进行咨询。

请注意，获取到 AK 和 SK 后，不要共享给他人，且在使用时要符合相关的使用规则和政策。

> Body 请求参数

```json
{
  "sid": "string"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|ak|cookie|string| 是 |业务方表示|
|sk|cookie|string| 是 |业务方秘钥|
|body|body|object| 否 |none|
|» sid|body|string| 是 |任务sid,提交任务时填写的值|

> 返回示例

> 成功

```json
{
  "errNo": 0,
  "errMsg": "succ",
  "data": {
    "sid": "BT|7aa93d45-4b09-4dcd-9861-aaa69e619b2e",
    "status": 1,
    "podIp": "10.106.129.88",
    "podPort": "8103",
    "progress": 1,
    "costTime": 66.59,
    "message": "ok",
    "queueNum": 0,
    "queueTotal": 0,
    "outputResult": [
      "cos://zyb-uxc-aigc-1253445850/batch_tasks/comfyui/output/9fb713ed-7ced-429c-9e53-70cdbc4a5feb.WEBP",
      "cos://zyb-uxc-aigc-1253445850/batch_tasks/comfyui/output/2e76ea9b-b7f7-4587-8196-a4b1c641e9a9.WEBP"
    ],
    "photoParameters": {
      "info": "ok",
      "parameters": {
        "2": {
          "_meta": {
            "title": "Checkpoint加载器(简易)"
          },
          "class_type": "CheckpointLoaderSimple",
          "inputs": {
            "ckpt_name": "POLY_AI_V2.safetensors"
          }
        },
        "3": {
          "_meta": {
            "title": "空Latent"
          },
          "class_type": "EmptyLatentImage",
          "inputs": {
            "batch_size": 2,
            "height": 1152,
            "width": 576
          }
        },
        "9": {
          "_meta": {
            "title": "IP适配模型加载器"
          },
          "class_type": "IPAdapterModelLoader",
          "inputs": {
            "ipadapter_file": "ip-adapter-plus-face_sdxl_vit-h.safetensors"
          }
        },
        "14": {
          "_meta": {
            "title": "LoRA加载器(仅模型)"
          },
          "class_type": "LoraLoaderModelOnly",
          "inputs": {
            "lora_name": "ip-adapter-faceid-plusv2_sdxl_lora.safetensors",
            "model": [
              "2",
              0
            ],
            "strength_model": 0.3
          }
        },
        "31": {
          "_meta": {
            "title": "CLIP视觉加载器"
          },
          "class_type": "CLIPVisionLoader",
          "inputs": {
            "clip_name": "CLIP-ViT-H-14-laion2B-s32B-b79K.safetensors"
          }
        },
        "32": {
          "_meta": {
            "title": "InsightFace加载器"
          },
          "class_type": "InsightFaceLoader",
          "inputs": {
            "provider": "CUDA"
          }
        },
        "33": {
          "_meta": {
            "title": "IP适配应用(FaceID)"
          },
          "class_type": "IPAdapterApplyFaceID",
          "inputs": {
            "attn_mask": [
              "186",
              0
            ],
            "clip_vision": [
              "31",
              0
            ],
            "end_at": 1,
            "faceid_v2": true,
            "image": [
              "66",
              0
            ],
            "insightface": [
              "32",
              0
            ],
            "ipadapter": [
              "9",
              0
            ],
            "model": [
              "14",
              0
            ],
            "noise": 0.9,
            "start_at": 0.3,
            "unfold_batch": false,
            "weight": 0.65,
            "weight_type": "original",
            "weight_v2": 0.5
          }
        },
        "44": {
          "_meta": {
            "title": "K采样器(高级Inspire)"
          },
          "class_type": "KSamplerAdvanced //Inspire",
          "inputs": {
            "add_noise": true,
            "batch_seed_mode": "incremental",
            "cfg": 8,
            "end_at_step": 10000,
            "latent_image": [
              "3",
              0
            ],
            "model": [
              "2",
              0
            ],
            "negative": [
              "222",
              1
            ],
            "noise_mode": "GPU(=A1111)",
            "noise_seed": "154517",
            "positive": [
              "222",
              0
            ],
            "return_with_leftover_noise": false,
            "sampler_name": "euler_ancestral",
            "scheduler": "normal",
            "start_at_step": 0,
            "steps": 30,
            "variation_seed": 0,
            "variation_strength": 0
          }
        },
        "45": {
          "_meta": {
            "title": "VAE解码"
          },
          "class_type": "VAEDecode",
          "inputs": {
            "samples": [
              "44",
              0
            ],
            "vae": [
              "46",
              0
            ]
          }
        },
        "46": {
          "_meta": {
            "title": "VAE加载器"
          },
          "class_type": "VAELoader",
          "inputs": {
            "vae_name": "sdxl_vae.safetensors"
          }
        },
        "65": {
          "_meta": {
            "title": "CLIP文本编码器(BNK)"
          },
          "class_type": "BNK_CLIPTextEncodeAdvanced",
          "inputs": {
            "clip": [
              "2",
              1
            ],
            "text": "(nsfw:1.5), (ugly), (duplicate), (morbid), (mutilated), out of frame, extra fingers, mutated hands, (poorly drawn hands), (poorly drawn face), (mutation), (deformed), blurry, (bad anatomy), (bad proportions), (extra limbs), cloned face, (disfigured), out of frame, ugly, extra limbs, (bad anatomy), gross proportions, (malformed limbs), (missing arms), (missing legs), (extra arms), (extra legs), mutated hands, (fused fingers), (too many fingers), (long neck), text, logo",
            "token_normalization": "mean",
            "weight_interpretation": "A1111"
          }
        },
        "66": {
          "_meta": {
            "title": "InsightFace预处理"
          },
          "class_type": "PrepImageForInsightFace",
          "inputs": {
            "crop_position": "center",
            "image": [
              "157",
              0
            ],
            "pad_around": true,
            "sharpening": 0
          }
        },
        "87": {
          "_meta": {
            "title": "CLIP文本编码器(BNK)"
          },
          "class_type": "BNK_CLIPTextEncodeAdvanced",
          "inputs": {
            "clip": [
              "2",
              1
            ],
            "text": [
              "204",
              0
            ],
            "token_normalization": "mean",
            "weight_interpretation": "A1111"
          }
        },
        "144": {
          "_meta": {
            "title": "字符串操作"
          },
          "class_type": "StringFunction|pysssss",
          "inputs": {
            "action": "append",
            "text_a": [
              "148",
              0
            ],
            "text_b": [
              "176",
              0
            ],
            "text_c": [
              "243",
              0
            ],
            "tidy_tags": "yes"
          }
        },
        "148": {
          "_meta": {
            "title": "String Literal"
          },
          "class_type": "String Literal",
          "inputs": {
            "string": "best quality, very aesthetic, absurdres"
          }
        },
        "157": {
          "_meta": {
            "title": "CLIP视觉图像处理"
          },
          "class_type": "PrepImageForClipVision",
          "inputs": {
            "crop_position": "top",
            "image": [
              "175",
              0
            ],
            "interpolation": "LANCZOS",
            "sharpening": 0
          }
        },
        "175": {
          "_meta": {
            "title": "加载图像"
          },
          "class_type": "LoadImage",
          "inputs": {
            "image": "dc10afc90871e4eff5966a552bc27189.webp",
            "upload": "image"
          }
        },
        "176": {
          "_meta": {
            "title": "WD14反推提示词"
          },
          "class_type": "WD14Tagger|pysssss",
          "inputs": {
            "character_threshold": 0.85,
            "exclude_tags": "bangs, earrings, jewelry, monochrome, male focus, grey background, green background, upper body, looking at viewer, portrait, white background, simple background",
            "image": [
              "175",
              0
            ],
            "model": "wd-v1-4-moat-tagger-v2",
            "replace_underscore": "1girl, 1boy, upper_body, looking_at_viewer, portrait, male_focus",
            "threshold": 0.2,
            "trailing_comma": "solo, long_hair, red_eyes, jewelry, red_hair, earrings, parted_lips"
          }
        },
        "186": {
          "_meta": {
            "title": "图像到遮罩"
          },
          "class_type": "ImageToMask",
          "inputs": {
            "channel": "red",
            "image": [
              "187",
              0
            ]
          }
        },
        "187": {
          "_meta": {
            "title": "加载图像"
          },
          "class_type": "LoadImage",
          "inputs": {
            "image": "POLY_MASK.png",
            "upload": "image"
          }
        },
        "204": {
          "_meta": {
            "title": "展示文本"
          },
          "class_type": "ShowText|pysssss",
          "inputs": {
            "text": [
              "144",
              0
            ]
          }
        },
        "205": {
          "_meta": {
            "title": "Latent按系数缩放"
          },
          "class_type": "LatentUpscaleBy",
          "inputs": {
            "samples": [
              "44",
              0
            ],
            "scale_by": 1.5,
            "upscale_method": "nearest-exact"
          }
        },
        "206": {
          "_meta": {
            "title": "K采样器"
          },
          "class_type": "KSampler",
          "inputs": {
            "cfg": 2,
            "denoise": 0.8,
            "latent_image": [
              "205",
              0
            ],
            "model": [
              "213",
              0
            ],
            "negative": [
              "222",
              1
            ],
            "positive": [
              "222",
              0
            ],
            "sampler_name": "euler_ancestral",
            "scheduler": "normal",
            "seed": "154517",
            "steps": 12
          }
        },
        "210": {
          "_meta": {
            "title": "VAE解码"
          },
          "class_type": "VAEDecode",
          "inputs": {
            "samples": [
              "206",
              0
            ],
            "vae": [
              "46",
              0
            ]
          }
        },
        "211": {
          "_meta": {
            "title": "保存图像"
          },
          "class_type": "SaveImage",
          "inputs": {
            "filename_prefix": "ComfyUI",
            "images": [
              "217",
              0
            ]
          }
        },
        "213": {
          "_meta": {
            "title": "LoRA加载器(仅模型)"
          },
          "class_type": "LoraLoaderModelOnly",
          "inputs": {
            "lora_name": "sdxl_lightning_8step_lora.safetensors",
            "model": [
              "33",
              0
            ],
            "strength_model": 1
          }
        },
        "217": {
          "_meta": {
            "title": "图像缩放"
          },
          "class_type": "ImageScale",
          "inputs": {
            "crop": "disabled",
            "height": 1152,
            "image": [
              "210",
              0
            ],
            "upscale_method": "lanczos",
            "width": 576
          }
        },
        "222": {
          "_meta": {
            "title": "ControlNet应用(高级)"
          },
          "class_type": "ControlNetApplyAdvanced",
          "inputs": {
            "control_net": [
              "224",
              0
            ],
            "end_percent": 1,
            "image": [
              "249",
              0
            ],
            "negative": [
              "65",
              0
            ],
            "positive": [
              "87",
              0
            ],
            "start_percent": 0,
            "strength": 0.8
          }
        },
        "224": {
          "_meta": {
            "title": "ControlNet加载器"
          },
          "class_type": "ControlNetLoader",
          "inputs": {
            "control_net_name": "OpenPoseXL2.safetensors"
          }
        },
        "228": {
          "_meta": {
            "title": "加载图像"
          },
          "class_type": "LoadImage",
          "inputs": {
            "image": "45f640f05e213476ae08558f9fbd2b06.png",
            "upload": "image"
          }
        },
        "243": {
          "_meta": {
            "title": "String Literal"
          },
          "class_type": "String Literal",
          "inputs": {
            "string": ""
          }
        },
        "249": {
          "_meta": {
            "title": "图像组合批次"
          },
          "class_type": "ImageBatch",
          "inputs": {
            "image1": [
              "228",
              0
            ],
            "image2": [
              "250",
              0
            ]
          }
        },
        "250": {
          "_meta": {
            "title": "加载图像"
          },
          "class_type": "LoadImage",
          "inputs": {
            "image": "45f640f05e213476ae08558f9fbd2b06.png",
            "upload": "image"
          }
        }
      }
    }
  }
}
```

```json
{
  "errNo": 1000,
  "errMsg": "错误信息",
  "data": {}
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» errNo|integer|true|none||none|
|» errMsg|string|true|none||错误信息描述|
|» data|object|true|none||none|
|»» sid|string|true|none||任务id|
|»» status|integer|true|none||任务状态|
|»» podIp|string|true|none||任务运行ip|
|»» podPort|string|true|none||任务运行端口|
|»» progress|integer|true|none||任务进度|
|»» costTime|number|true|none||任务耗时|
|»» message|string|true|none||任务信息（错误信息展示）|
|»» queueNum|integer|true|none||当前任务排队序列|
|»» queueTotal|integer|true|none||任务总序列|
|»» outputResult|[string]|true|none||输出结果|
|»» photoParameters|object|true|none||图片信息|
|»»» info|string|true|none||none|
|»»» parameters|object|true|none||none|

#### 枚举值

|属性|值|
|---|---|
|errNo|0|
|errNo|3002|
|errNo|3103|
|errNo|5000|
|status|1|
|status|2|
|status|100|
|status|200|
|status|999|
|status|1000|

# 数据模型

