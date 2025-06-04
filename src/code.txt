import { JSX, useState } from "react";

const labels = ["v1", "v2", "v3", "v4"];
const positions: { x: number; y: number }[] = [
    { x: 70, y: 70 },
    { x: 210, y: 70 },
    { x: 70, y: 210 },
    { x: 210, y: 210 },
];

const edges: Record<string, JSX.Element> = {
    // v1 → v2
    "v1-v2-1": (
        <line
            x1={positions[0].x}
            y1={positions[0].y + 5}
            x2={positions[1].x - 20}
            y2={positions[1].y + 5}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v1-v2-2": (
        <line
            x1={positions[0].x}
            y1={positions[0].y - 5}
            x2={positions[1].x - 20}
            y2={positions[1].y - 5}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),

    // v2 → v1
    "v2-v1-1": (
        <line
            x1={positions[1].x}
            y1={positions[1].y}
            x2={positions[0].x + 20}
            y2={positions[0].y}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v2-v1-2": (
        <line
            x1={positions[1].x}
            y1={positions[1].y + 10}
            x2={positions[0].x + 20}
            y2={positions[0].y + 10}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),

    // v1 → v3
    "v1-v3-1": (
        <line
            x1={positions[0].x + 5}
            y1={positions[0].y}
            x2={positions[2].x + 5}
            y2={positions[2].y - 20}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v1-v3-2": (
        <line
            x1={positions[0].x - 5}
            y1={positions[0].y}
            x2={positions[2].x - 5}
            y2={positions[2].y - 20}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),

    // v3 → v1
    "v3-v1-1": (
        <line
            x1={positions[2].x}
            y1={positions[2].y}
            x2={positions[0].x}
            y2={positions[0].y + 20}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v3-v1-2": (
        <line
            x1={positions[2].x + 10}
            y1={positions[2].y}
            x2={positions[0].x + 10}
            y2={positions[0].y + 20}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),

    // v2 → v4
    "v2-v4-1": (
        <line
            x1={positions[1].x + 5}
            y1={positions[1].y}
            x2={positions[3].x + 5}
            y2={positions[3].y - 20}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v2-v4-2": (
        <line
            x1={positions[1].x - 5}
            y1={positions[1].y}
            x2={positions[3].x - 5}
            y2={positions[3].y - 20}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),

    // v4 → v2
    "v4-v2-1": (
        <line
            x1={positions[3].x}
            y1={positions[3].y}
            x2={positions[1].x}
            y2={positions[1].y + 20}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v4-v2-2": (
        <line
            x1={positions[3].x + 10}
            y1={positions[3].y}
            x2={positions[1].x + 10}
            y2={positions[1].y + 20}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),

    // v3 → v4
    "v3-v4-1": (
        <line
            x1={positions[2].x}
            y1={positions[2].y + 5}
            x2={positions[3].x - 20}
            y2={positions[3].y + 5}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v3-v4-2": (
        <line
            x1={positions[2].x}
            y1={positions[2].y - 5}
            x2={positions[3].x - 20}
            y2={positions[3].y - 5}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),

    // v4 → v3
    "v4-v3-1": (
        <line
            x1={positions[3].x}
            y1={positions[3].y}
            x2={positions[2].x + 20}
            y2={positions[2].y}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v4-v3-2": (
        <line
            x1={positions[3].x}
            y1={positions[3].y + 10}
            x2={positions[2].x + 20}
            y2={positions[2].y + 10}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v1-v4-1": (
        <line
            x1={positions[0].x - 5}
            y1={positions[0].y + 3}
            x2={positions[3].x - 15}
            y2={positions[3].y - 7}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v1-v4-2": (
        <line
            x1={positions[0].x + 5}
            y1={positions[0].y}
            x2={positions[3].x - 5}
            y2={positions[3].y - 13}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),

    // v4 → v1
    "v4-v1-1": (
        <line
            x1={positions[3].x}
            y1={positions[3].y}
            x2={positions[0].x + 12}
            y2={positions[0].y + 15}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v4-v1-2": (
        <line
            x1={positions[3].x - 10}
            y1={positions[3].y + 5}
            x2={positions[0].x}
            y2={positions[0].y + 15}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),

    // v2 → v3
    "v2-v3-1": (
        <line
            x1={positions[1].x - 5}
            y1={positions[1].y + 5}
            x2={positions[2].x + 7}
            y2={positions[2].y - 13}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v2-v3-2": (
        <line
            x1={positions[1].x + 10}
            y1={positions[1].y + 10}
            x2={positions[2].x + 17}
            y2={positions[2].y - 3}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),

    // v3 → v2
    "v3-v2-1": (
        <line
            x1={positions[2].x - 5}
            y1={positions[2].y - 5}
            x2={positions[1].x - 13}
            y2={positions[1].y + 8}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v3-v2-2": (
        <line
            x1={positions[2].x + 5}
            y1={positions[2].y + 5}
            x2={positions[1].x - 5}
            y2={positions[1].y + 15}
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v1-v1-1": (
        <path
            d={`
      M ${positions[0].x - 5} ${positions[0].y - 10} 
      C ${positions[0].x - 30} ${positions[0].y - 40}, 
        ${positions[0].x + 30} ${positions[0].y - 40}, 
        ${positions[0].x + 5} ${positions[0].y - 15}
    `}
            fill="none"
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v1-v1-2": (
        <path
            d={`
      M ${positions[0].x - 5} ${positions[0].y - 10} 
      C ${positions[0].x - 30} ${positions[0].y - 40}, 
        ${positions[0].x - 50} ${positions[0].y + 40}, 
        ${positions[0].x - 15} ${positions[0].y}
    `}
            fill="none"
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v2-v2-1": (
        <path
            d={`
      M ${positions[1].x - 5} ${positions[1].y - 10} 
      C ${positions[1].x - 30} ${positions[1].y - 40}, 
        ${positions[1].x + 30} ${positions[1].y - 40}, 
        ${positions[1].x + 5} ${positions[1].y - 15}
    `}
            fill="none"
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v2-v2-2": (
        <path
            d={`
      M ${positions[1].x + 5} ${positions[1].y - 10} 
      C ${positions[1].x + 30} ${positions[1].y - 40}, 
        ${positions[1].x + 50} ${positions[1].y + 40}, 
        ${positions[1].x + 15} ${positions[1].y}
    `}
            fill="none"
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v3-v3-1": (
        <path
            d={`
      M ${positions[2].x - 10} ${positions[2].y - 10} 
      C ${positions[2].x - 30} ${positions[2].y - 40}, 
        ${positions[2].x - 30} ${positions[2].y + 50}, 
        ${positions[2].x - 5} ${positions[2].y + 10}
    `}
            fill="none"
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v3-v3-2": (
        <path
            d={`
      M ${positions[2].x} ${positions[2].y + 15} 
      C ${positions[2].x + 10} ${positions[2].y + 40}, 
        ${positions[2].x + 30} ${positions[2].y + 40}, 
        ${positions[2].x + 15} ${positions[2].y + 15}
    `}
            fill="none"
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v4-v4-1": (
        <path
            d={`
      M ${positions[3].x - 5} ${positions[3].y + 10} 
      C ${positions[3].x - 30} ${positions[3].y + 40}, 
        ${positions[3].x + 30} ${positions[3].y + 40}, 
        ${positions[3].x + 5} ${positions[3].y + 15}
    `}
            fill="none"
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
    "v4-v4-2": (
        <path
            d={`
      M ${positions[3].x + 5} ${positions[3].y - 10} 
      C ${positions[3].x + 30} ${positions[3].y - 40}, 
        ${positions[3].x + 50} ${positions[3].y + 40}, 
        ${positions[3].x + 15} ${positions[3].y}
    `}
            fill="none"
            stroke="black"
            markerEnd="url(#arrowhead)"
        />
    ),
};

const App = () => {
    const [edgesIdxs, setEdgesIdxs] = useState<string[]>([]);
    const renderRowInputs = (rowLabel: string) => {
        return labels.map((colLabel) => (
            <td key={`${rowLabel}-${colLabel}`}>
                <input
                    type="number"
                    className="border border-gray-400 w-12 h-12 text-center"
                    placeholder="0"
                    id={`${rowLabel}-${colLabel}`}
                    min={0}
                    max={2}
                    step={1}
                    onInput={(e) => {
                        const input = e.target as HTMLInputElement;
                        if (input.value === "") {
                            setEdgesIdxs((prev) => {
                                let newData = [...prev];

                                newData = newData.filter((item) => !item.includes(`${rowLabel}-${colLabel}`));
                                return newData;
                            });
                        }
                        const value = parseInt(input.value, 10);
                        if (![0, 1, 2].includes(value)) {
                            input.value = "";
                        } else {
                            setEdgesIdxs((prev) => {
                                let newData = [...prev];
                                if (value === 0) {
                                    newData = newData.filter(
                                        (item) => !item.includes(`${rowLabel}-${colLabel}`)
                                    );
                                    return newData;
                                }
                                if (value === 1) {
                                    newData = newData.filter(
                                        (item) => !item.includes(`${rowLabel}-${colLabel}`)
                                    );
                                    newData.push(`${rowLabel}-${colLabel}-1`);
                                    return newData;
                                }
                                if (value === 2) {
                                    newData.push(`${rowLabel}-${colLabel}-1`);
                                    newData.push(`${rowLabel}-${colLabel}-2`);
                                    return newData;
                                }
                                return newData;
                            });
                        }
                    }}
                />
            </td>
        ));
    };

    return (
        <div className="flex flex-col items-center  h-screen bg-gray-50 space-y-6">
            <div className="flex justify-center mt-8">
                <table className="table-fixed border-collapse border border-gray-400">
                    <thead>
                        <tr>
                            <th className="border border-gray-400 w-12 h-12"></th>
                            {labels.map((col) => (
                                <th
                                    key={col}
                                    className="border border-gray-400 w-12 h-12 text-center font-semibold bg-gray-100"
                                >
                                    {col}
                                </th>
                            ))}
                        </tr>
                    </thead>
                    <tbody>
                        {labels.map((row) => (
                            <tr key={row}>
                                <th className="border border-gray-400 text-center font-semibold bg-gray-100">
                                    {row}
                                </th>
                                {renderRowInputs(row)}
                            </tr>
                        ))}
                    </tbody>
                </table>
            </div>
            <svg
                width={300}
                height={300}
                className="border-2 border-black"
            >
                <defs>
                    <marker
                        id="arrowhead"
                        markerWidth="10"
                        markerHeight="7"
                        refX="10"
                        refY="3.5"
                        orient="auto"
                        markerUnits="strokeWidth"
                    >
                        <polygon
                            points="0 0, 10 3.5, 0 7"
                            fill="black"
                        />
                    </marker>
                </defs>
                {positions.map((pos, idx) => (
                    <g>
                        <circle
                            cx={pos.x}
                            cy={pos.y}
                            r={20}
                            fill="blue"
                        />
                        <text
                            x={pos.x + 20}
                            y={pos.y - 20}
                            fill="black"
                            textAnchor="middle"
                            fontWeight={700}
                        >
                            {`v${idx + 1}`}
                        </text>
                    </g>
                ))}
                {edgesIdxs.map((edgeIdx) => edges[edgeIdx])}
            </svg>
        </div>
    );
};

export default App;
