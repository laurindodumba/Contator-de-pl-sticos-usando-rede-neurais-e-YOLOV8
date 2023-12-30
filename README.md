## PROJETO CONTADOR DE GARRAFAS DE ÁGUA COM YOLOV8


✍ Desenvolver uma aplicação inteligente que faça a contagem das garrafas de água para indústria é grande tarefa que tem seu impacto positivo no ponto de vista de custo e benéficio para, isto é reduzindo na implementação de sensores que poderia realizar este tipo de  contagem.
E tendo em conta este ponto, através da intelegência Artificial é possível criar aplicar técnicas de metódos que podem ser muito bem usado neste tipo de situações para melhorar nos processos.

#
# TÉCNICAS USADAS :
- Baixei uma base de dados pré treinada código abaixo.
  


  Execute o seguinte comando no terminal:

```bash

!pip install -r requirements.txt

!git clone https://github.com/MuhammadMoinFaisal/YOLOv7-DeepSORT-Object-Tracking.git


%cd /content/YOLOv7-DeepSORT-Object-Tracking


!gdown "https://drive.google.com/uc?id=11ZSZcG-bcbueXZC3rN08CM0qqX3eiHxf&confirm=t"


!unzip 'deep_sort_pytorch.zip'

%%bash
wget -P /content/YOLOv7-DeepSORT-Object-Tracking https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt


!gdown https://drive.google.com/uc?id=13lQL7Aodcc4lMa-x1LicrKnhnBsFp2-2


!gdown https://drive.google.com/uc?id=1Gcba9JsRR5CDb2btN7WhZe0Y_42-ZvNr


%cd /content/YOLOv7-DeepSORT-Object-Tracking

!pwd

!gdown https://drive.google.com/uc?id=1pMPypK9A_zIDLYD_VykCN44KQwB4RVSI


!python bottle_counting_test1.py --weights 'yolov7.pt'  --img 640  --source video3.mp4  --classes 39 --conf 0.25


!rm "/content/result_compressed.mp4"



from IPython.display import HTML
from base64 import b64encode
import os

# Entrada  dos dados para serem treinados
save_path = '/content/YOLOv7-DeepSORT-Object-Tracking/runs/detect/exp/video3.mp4'

# Compressão do vídeo
compressed_path = "/content/result_compressed.mp4"

os.system(f"ffmpeg -i {save_path} -vcodec libx264 {compressed_path}")

# Apresentação do vídeo
mp4 = open(compressed_path,'rb').read()
data_url = "data:video/mp4;base64," + b64encode(mp4).decode()
HTML("""
<video width=400 controls>
      <source src="%s" type="video/mp4">
</video>
""" % data_url)

