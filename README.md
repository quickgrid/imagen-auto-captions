# imagen-auto-captions

Conditional and unconditional imagen training with just images. Captions and embedding are generated automatically which are used to train text conditional imagen model.

Just images are needed for text conditional training. Captions are generated with `BLIP` captions and vqa pretrained model in text files. 

A predefined set of questions can be asked for each training image with vqa. These query results are appended to caption text to get more accurate description of image which may help get more refined results during training and sampling.

These captions are passed to chosen `T5` model which generates text embeddings and masks. The embedding and mask are padded to chosen `MAX_LENGTH`. These are then saved in `npy` files. 

A custom dataloader reads `(image, text embedding, text mask)` which are passed to imagen trainer.

- `imagen-pytorch` folder is modified version of, https://github.com/lucidrains/imagen-pytorch.
- `blip` folder is modified version of, https://github.com/salesforce/BLIP.


## TODO

- Check if `BLIP` or another feature extraction method can work in place of T5.
