# HW
# 一球从 100 米的高度自由落体（忽略空气阻力），每次落地后反跳回原高度的一半，再落下。 求：（1）第10次掉下并反弹到最高点时，反弹了多高？此时球一共经过多少米，运动了多少时间？ （1）第n次掉下并反弹到最高点时，反弹了多高？此时球一共经过多少米，运动了多少时间？  需要写程序实现，请提交可以执行的python程序文件和word版本的文字总结和解
import math

def ball(n, h0=100, g=9.8):
    
    fantan_h = h0 * (0.5 ** n)  # 反弹高度

    zong_l = h0  # 初始下落的路程
    
    for i in range(1, n):
        zong_l += 2 * h0 * (0.5 ** i)  # 每次弹起并+下落的路程
   
    zong_l += h0 * (0.5 ** n)# 总路程
   
    zong_t = math.sqrt(2 * h0 / g)  # 初始下落时间
    
    for i in range(1, n):
        hi = h0 * (0.5 ** i)  # 第i次弹起的高度
        
        zong_t += 2 * math.sqrt(2 * hi / g)  # 弹起+下落时间
        
    hi_n = h0 * (0.5 ** n)  # 最后一次弹起的时间
    
    zong_t += math.sqrt(2 * hi_n / g)  # 总时间
    
    return fantan_h, zong_l, zong_t

if __name__ == "__main__":
    # （1）第10次的情况
    n1 = 10
    h1, l1, t1 = ball(n1)
    print(f"（1）第{n1}次反弹的高度：{h1:.4f} 米")
    print(f"    总路程：{l1:.4f} 米")
    print(f"    总时间：{t1:.4f} 秒")
    
    # （2）输入n的情况
    n2 = int(input("\n请输入问题（2）中的n值："))
    h2, l2, t2 = ball(n2)
    print(f"（2）第{n2}次反弹的高度：{h2:.4f} 米")
    print(f"    总路程：{l2:.4f} 米")
    print(f"    总时间：{t2:.4f} 秒")
