# Genshindownscale
Use this in Shizuku or brevent
•
•
•
a=/storage/emulated/0/Android/data/com.miHoYo.GenshinImpact/files/hardware_model_config.json
b='{\n    "configs": [\n        {\n            "hardwareModel": "*",\n            "littleCoreCount": 0,\n            "bigCoreCount": 8,\n            "littleCoreMask": 255,\n            "bigCoreMask": 0,\n            "openglFlag": x\n        }\n    ]\n}'
if [ "$api" = opengl ];then
  rm -rf "$a"
  printf "$b"|sed "s/\*/$(getprop ro.product.manufacturer) $(getprop ro.product.model)/g;s/x/1/g">"$a"
else
  rm -rf "$a"
  printf "$b"|sed "s/\*/$(getprop ro.product.manufacturer) $(getprop ro.product.model)/g;s/x/0/g">"$a"
fi
for c in /storage/emulated/0/Android/data/com.miHoYo.GenshinImpact/files/vulkan_gpu_list_config.txt /storage/emulated/0/Android/data/com.miHoYo.GenshinImpact/files/vulkan_gpu_list_config_engine.txt;do
  rm -rf "$c"
  if [ "$api" = opengl ];then
    printf "$(dumpsys SurfaceFlinger|grep GLES:|cut -f2 -d,|grep -ov '^ ')">"$c"fi
  •
  •|
  •|
  REPLACE "$api" to vulkan If you want best performance at your phone
