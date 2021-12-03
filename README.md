# coco-datasets-balloon

### Original via format balloon_dataset(https://github.com/matterport/Mask_RCNN/releases/download/v2.1/balloon_dataset.zip)

### Use VIA2COCO(https://github.com/woctezuma/VIA2COCO) convert to coco format

### Create coco annotations
```
import convert as via2coco

data_path = '/content/VIA2COCO/'

for keyword in ['train', 'val']:

  input_dir = data_path + 'balloon/' + keyword + '/'
  input_json = input_dir + 'via_region_data.json'
  categories = ['balloon']
  super_categories = ['N/A']
  output_json = input_dir + 'custom_' + keyword + '.json'

  print('Converting {} from VIA format to COCO format'.format(input_json))

  coco_dict = via2coco.convert(
      imgdir=input_dir,
      annpath=input_json,
      categories=categories,
      super_categories=super_categories,
      output_file_name=output_json,
      first_class_index=first_class_index,
  )
```

### move files
```
!mkdir -p /content/data/custom/annotations/

!mv /content/VIA2COCO/balloon/train/custom_train.json /content/data/custom/annotations/custom_train.json
!mv /content/VIA2COCO/balloon/val/custom_val.json /content/data/custom/annotations/custom_val.json

!mkdir -p /content/data/custom/train2017/

!mv /content/VIA2COCO/balloon/train/*.jpg /content/data/custom/train2017/

!mkdir -p /content/data/custom/val2017/

!mv /content/VIA2COCO/balloon/val/*.jpg /content/data/custom/val2017/
```
