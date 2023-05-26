# StyleGAN2-ada_Toonify
My graduation project with StyleGAN2-ada & Toonify

StyleGAN2-ada paper : https://arxiv.org/abs/2006.06676

StyleGAN2-ada github : https://github.com/NVlabs/stylegan2-ada-pytorch

Toonify github : https://github.com/justinpinkney/toonify


![image](https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/93dbcaba-28db-4f30-87b0-baea3a77477b)


- mapping own data

```
!python projector_custom.py --outdir=./out/myungsoo --target=./realign1024x1024/00000/myungsoo.png --network=./pretrained/ffhq.pkl --save-video=False --verbose=True --extend=True --num-steps=5000
```

#click option

#('--network', 'network_pkl', help='Network pickle filename', required=True)

#('--target', 'target_fname', help='Target image file to project to', required=True, metavar='FILE')

#('--num-steps',              help='Number of optimization steps', type=int, default=1000, show_default=True)

#('--seed',                   help='Random seed', type=int, default=303, show_default=True)

#('--save-video',             help='Save an mp4 video of optimization progress', type=bool, default=True, show_default=True)

#('--outdir',                 help='Where to save the output images', required=True, metavar='DIR')

#('--verbose',                help='verbose', type=bool, default=True)

#('--extend',                help='Want to project with extended w(18vectors)', type=bool, default=False))

- Original Image
<img src = "https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/dee34ac2-55a7-41ef-b146-fdab48a5e2f8" width="50%" height="50%">

- mapping preprocessing

  - Crop & Resize (1024 x 1024)
  <img src = "https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/839b0381-456a-44df-897f-8fc61db02e49" width="30%" height="30%">


  - landmark & align (same with FFHQ preprocessing)
  <img src = "https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/c6c7b8ef-2b58-4ddb-8c1f-c623c67687e1" width="30%" height="30%">


- mapping with W(1,) or W(18,) #projector_custom 'extend' parameter
  - with W(1,)
  <img src = "https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/55794cb9-d3c4-4926-82fe-efd07a87846f" width="30%" height="30%">
  
  
  - with W(18,)
    - epoch 1000
    <img src = "https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/0346770e-182e-4896-ab60-d99e5f546847" width="30%" height="30%">
    
    - epoch 5000
    <img src = "https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/da9fc4bb-9819-40a1-826c-36cffda5d4ca" width="30%" height="30%">


- mapping with W(18,) has a problem
  - Visual fidelity is higher, but semantic fidelity is lower
  - W(1,)로 mapping하면 synthesis시 퀄리티가 떨어지지만 mapping결과인 18개의 벡터의 facial semantic이 잘 mapping됨
  - W(18,)로 mapping하면 synthesis시 퀄리티 있게 나오지만 vecotr의 facial sematic이 감소하여 vector mixing이 잘 안됨   


- Modify Image

  - Used Image Information

    - from random z -> mapped W (very semantic W vectors)
    <img src = "![image](https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/893f8307-137a-448b-bd28-a527edd6a78a)
" width="50%" height="50%">

    - specified images's projected W (less semantic W vectors)
    <img src = "https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/da9fc4bb-9819-40a1-826c-36cffda5d4ca" width="30%" height="30%">

  - Method

    - style mixing : mix W vectors

    - blended Network : blend two different style of Generator's layers (architecture of PGGAN)

