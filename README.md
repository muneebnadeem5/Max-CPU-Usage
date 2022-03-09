# Max-CPU-Usage
CPau usage from a service OR a sub service


------------------------------
MaxCPU=$(top -b -n2 -p 1 | fgrep "Cpu(s)" | tail -1 | awk -F'id,' -v prefix="$prefix" '{ split($1, vs, ","); v=vs[length(vs)]; sub("%", "", v); printf "%s%.1f%%\n", prefix, 100 - v }' |tr -d '%')

        if [ "${MaxCPU%%.*}" -ge "90" ];
        then
                        echo CPU is going high 90%.
                        echo "" >> /tmp/top5-process.txt
                        echo "" >> /tmp/top5-process.txt
                        echo "=============================" >> /tmp/top5-process.txt
                        echo `date` >> /tmp/top5-process.txt
                        echo "=============================" >> /tmp/top5-process.txt
                        echo "" >> /tmp/top5-process.txt
                        echo $MaxCPU >> /tmp/top5-process.txt
                        ps aux | sort -nrk 3,3 | head -n 5 >> /tmp/top5-process.txt

        else
                        echo CPU is less than 90%.
                        echo $MaxCPU
        fi
