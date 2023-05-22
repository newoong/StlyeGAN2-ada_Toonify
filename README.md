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

- mapping preprocessing
  - Crop & Resize (1024 x 1024)
  - ![target_only_crop](https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/d0ce6586-240e-484a-bcc1-904c7f9769d3)
  - ![proj_only_crop](https://github.com/newoong/StyleGAN2-ada_Toonify/assets/94604584/f2db6c9e-f571-447f-ae41-95106f7a6143)

