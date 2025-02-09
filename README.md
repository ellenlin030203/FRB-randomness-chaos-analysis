# FRB-randomness-chaos-analysis
FRB randomness-chaos analysis

Part one. <br>

Load data<be>

Part two. <be>

found out the most number of bursts and second most number of bursts group<br>

Part three.<br>

found the parameters we wanted arrival time, burst energy, and center frequency<br>
 
Part four.<br>

calculate waiting time, energy change, center frequency change<br>

claculate LLE at this place<br>

Part five. <br>

defines the function we need<br>

1. ApEn function
def ApEn(U, m, r) -> float:
    """Approximate_entropy."""

    def _maxdist(x_i, x_j):
        return max([abs(ua - va) for ua, va in zip(x_i, x_j)])

    def _phi(m):
        x = [[U[j] for j in range(i, i + m - 1 + 1)] for i in range(N - m + 1)]
        C = [
            len([1 for x_j in x if _maxdist(x_i, x_j) <= r]) / (N - m + 1.0)
            for x_i in x
        ]
        return (N - m + 1.0) ** (-1) * sum(np.log(C))

    N = len(U)

    return abs(_phi(m + 1) - _phi(m))
2. PI function
def PI(original, shuffle):
    ApEn_max = max(original)
    ApEn_shuffle_max = np.array(shuffle.max())
    PI = ApEn_max/ApEn_shuffle_max
    return np.mean(PI), np.std(PI)
Part six.<br>

calculate ApEn on our array<br>

original/shuffle(N=100)<br>

Part seven.<br>

calculate PI<br>

