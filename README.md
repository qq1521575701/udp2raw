# udp2raw
    docker pull jasperhale/udp2raw:latest

# udp2raw.conf
    # -s 服务端模式
    # -l 监听地址（伪装端口）
    # -r 转发到真实 UDP 服务
    # -k 密码（客户端必须一致）
    -s
    -l 0.0.0.0:900
    -r 127.0.0.1:51820
    -k 123456
    --cipher-mode xor
    --auth-mode simple
    --raw-mode faketcp
    --seq-mode 3
    --lower-level auto

# 运行
    docker run -d --name udp2raw --privileged --network=host -v $(pwd)/udp2raw.conf:/config.conf jasperhale/udp2raw:latest

# win 客户端运行
    udp2raw_mp_wepoll.exe -c -l 127.0.0.1:51820 -r 35.241.90.48:900 -k 123456 --raw-mode faketcp --cipher-mode xor --auth-mode simple
