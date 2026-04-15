  python train.py --data coco.yaml --epochs 300 --weights '' --cfg yolov5n.yaml --batch-size 128
  
  python train.py --data VOC.yaml --weights yolov5n.pt --epochs 100 --batch-size 128                        


  python train.py --data VOC.yaml --weights '' --cfg yolov5n.yaml --epochs 100 --batch-size 128                        
  
  python train.py --data VOC.yaml --epochs 100 --weights yolo5n.pt --batch-size 128